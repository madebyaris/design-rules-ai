# View Transitions

The View Transitions API gives you native crossfades and shared-element morphs between page states — for free, with no JS animation libraries. Browser support: Chrome 111+ (same-document), Chrome 126+ (cross-document MPA), Safari 18+, Firefox in development.

Always honor `prefers-reduced-motion` (the API does this automatically when properly used).

---

## Single-page (SPA) transitions

Wrap any DOM update in `document.startViewTransition`:

```js
function navigate(html) {
  if (!document.startViewTransition) {
    // Fallback: just swap content
    document.querySelector('main').innerHTML = html;
    return;
  }
  document.startViewTransition(() => {
    document.querySelector('main').innerHTML = html;
  });
}
```

The browser snapshots the page before and after, then crossfades between them. Default duration: ~300ms.

---

## Multi-page (MPA) transitions — cross-document

Opt the whole site in (works between full page loads):

```css
@view-transition {
  navigation: auto;
}
```

That's it. Same-origin navigations now crossfade. No JavaScript required.

---

## Shared element morphs (the magic)

Mark elements that should morph between states with the same `view-transition-name`:

```css
/* On the list page */
.product-card[data-id="42"] {
  view-transition-name: product-42;
}

/* On the detail page */
.product-hero {
  view-transition-name: product-42;
}
```

The browser morphs position, size, and shape. Critical: `view-transition-name` must be **unique per page snapshot**. Don't put it on multiple visible elements at the same time.

For a list of N items, generate names dynamically:

```jsx
{items.map(item => (
  <a key={item.id} style={{ viewTransitionName: `card-${item.id}` }} href={`/items/${item.id}`}>
    {item.title}
  </a>
))}
```

---

## Customizing the animation

Override the default with CSS keyframes targeting `::view-transition-old` and `::view-transition-new`:

```css
::view-transition-old(root),
::view-transition-new(root) {
  animation-duration: 300ms;
  animation-timing-function: cubic-bezier(0.16, 1, 0.3, 1);
}

/* Slide instead of fade */
::view-transition-old(root) {
  animation: slide-out 300ms ease-in;
}
::view-transition-new(root) {
  animation: slide-in 300ms ease-out;
}

@keyframes slide-out { to { transform: translateX(-100%); opacity: 0; } }
@keyframes slide-in  { from { transform: translateX(100%); opacity: 0; } }
```

---

## Common recipes

### Theme toggle (light ↔ dark)

```js
function toggleTheme() {
  const transition = document.startViewTransition(() => {
    document.documentElement.dataset.theme =
      document.documentElement.dataset.theme === 'dark' ? 'light' : 'dark';
  });

  // Optional: ripple from the toggle button
  transition.ready.then(() => {
    const { x, y } = getToggleButtonCenter();
    document.documentElement.animate(
      [
        { clipPath: `circle(0% at ${x}px ${y}px)` },
        { clipPath: `circle(150% at ${x}px ${y}px)` }
      ],
      { duration: 500, pseudoElement: '::view-transition-new(root)' }
    );
  });
}
```

### Modal open/close

Mark the trigger and the modal with the same name:

```css
.open-button { view-transition-name: modal-source; }
.modal-content { view-transition-name: modal-source; }
```

Browser morphs between them. Combine with `<dialog>` for free a11y.

### List → detail (cards)

See "shared element morphs" above. Each card and its detail-page hero share a name.

---

## Reserved names (recommended convention)

| Name | Use |
|------|-----|
| `page-root` | Root container (defaults to entire page) |
| `hero` | Hero / header element |
| `nav` | Persistent navigation across pages |
| `card-{id}` | List item ↔ detail morph |
| `theme-toggle` | Theme switch ripple |
| `modal-{id}` | Modal source ↔ modal content |

---

## Pitfalls

- **Names must be unique per snapshot.** Two visible elements with the same name = browser falls back to no animation and warns in console.
- **Don't animate everything.** Default page-root crossfade is usually enough. Add shared-element names only for hero pieces.
- **Off-screen elements still get snapshotted.** Use `view-transition-class` (newer) for grouped behavior, or omit names for elements that shouldn't morph.
- **Layout-shifting transitions look bad.** Keep dimensions stable when possible.
- **`prefers-reduced-motion`** is honored automatically when you use the API; for custom keyframes, wrap with the media query manually.
