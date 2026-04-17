# shadcn/ui — Components Cheat Sheet

**Canonical docs:** https://ui.shadcn.com/docs/components

**What to copy from this system:** composition primitives, accessible Radix UI foundations, copy-paste-not-package model.

---

## When to choose shadcn/ui

- React/Next.js project.
- You want unstyled, accessible primitives you can theme.
- Tailwind CSS already in stack (or you'll add it).
- You're OK pasting components into your repo (not installing as a package).

---

## Component patterns to emulate

| Component | What's good about it |
|-----------|---------------------|
| **Button** | `cva` variant API, asChild prop for composition. |
| **Dialog** | Radix primitive — focus trap, ESC handling, scroll lock for free. |
| **DropdownMenu** | Full keyboard nav, nested menus, checkbox/radio items built in. |
| **Form** | React Hook Form + Zod integration, accessible labels, error rendering. |
| **DataTable** | Tanstack Table integration, sortable/filterable/paginated. |
| **Toast (Sonner)** | Stacked, swipeable, prefers-reduced-motion aware. |
| **Combobox** | Headless `cmdk` foundation, fuzzy search baked in. |

---

## CSS conventions

- Tailwind utilities, no separate CSS files.
- Theme via CSS custom properties on `:root` and `.dark`:

```css
:root {
  --background: 0 0% 100%;
  --foreground: 0 0% 3.9%;
  --primary: 240 5.9% 10%;
  --primary-foreground: 0 0% 98%;
}
.dark {
  --background: 0 0% 3.9%;
  --foreground: 0 0% 98%;
}
```

Note: shadcn historically uses HSL. For new projects, prefer OKLCH (see `tokens-modern.css`).

---

## Install (CLI)

```bash
npx shadcn@latest init
npx shadcn@latest add button dialog form
```

Components land in `components/ui/`. Edit them freely — they're yours.

---

## Composition pattern

shadcn favors composition over configuration:

```tsx
<Dialog>
  <DialogTrigger asChild><Button>Open</Button></DialogTrigger>
  <DialogContent>
    <DialogHeader>
      <DialogTitle>Are you sure?</DialogTitle>
    </DialogHeader>
    <DialogFooter>
      <Button variant="ghost">Cancel</Button>
      <Button variant="destructive">Delete</Button>
    </DialogFooter>
  </DialogContent>
</Dialog>
```

Slot-based composition lets you replace any layer without breaking accessibility.

---

## What to AVOID copying

- Don't install shadcn primitives as a package (defeats the point — paste them in).
- Don't fight the variant system; if you need many variants, use `cva` properly.
- Don't skip the `asChild` pattern — it's how you keep semantic HTML when wrapping.
