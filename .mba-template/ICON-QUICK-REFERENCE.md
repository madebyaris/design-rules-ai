# Icon Quick Reference

## ⚠️ CRITICAL RULE

**NEVER generate SVG code from scratch. This wastes massive amounts of tokens.**

**ALWAYS use icon libraries instead.**

## Quick Setup

### Font Awesome (Easiest)
```html
<!-- Add to <head> -->
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">

<!-- Use anywhere -->
<i class="fa-solid fa-user"></i>
<i class="fa-solid fa-heart"></i>
<i class="fa-solid fa-magnifying-glass"></i>
```

### Heroicons (React/Tailwind)
```bash
npm install @heroicons/react
```

```jsx
import { UserIcon, HeartIcon, MagnifyingGlassIcon } from '@heroicons/react/24/outline'

<UserIcon className="h-6 w-6" />
```

### Lucide (Modern)
```html
<script src="https://unpkg.com/lucide@latest"></script>

<i data-lucide="user"></i>
<i data-lucide="heart"></i>

<script>lucide.createIcons();</script>
```

## Common Icons

### Actions
| Icon | Font Awesome | Heroicons | Lucide |
|------|-------------|-----------|--------|
| Close | `fa-xmark` | `XMarkIcon` | `x` |
| Add | `fa-plus` | `PlusIcon` | `plus` |
| Edit | `fa-pen` | `PencilIcon` | `pencil` |
| Save | `fa-floppy-disk` | `DocumentCheckIcon` | `save` |
| Delete | `fa-trash` | `TrashIcon` | `trash-2` |
| Search | `fa-magnifying-glass` | `MagnifyingGlassIcon` | `search` |
| Filter | `fa-filter` | `FunnelIcon` | `filter` |
| Settings | `fa-gear` | `Cog6ToothIcon` | `settings` |
| Menu | `fa-bars` | `Bars3Icon` | `menu` |
| More | `fa-ellipsis-vertical` | `EllipsisVerticalIcon` | `more-vertical` |

### Navigation
| Icon | Font Awesome | Heroicons | Lucide |
|------|-------------|-----------|--------|
| Home | `fa-house` | `HomeIcon` | `home` |
| Back | `fa-arrow-left` | `ArrowLeftIcon` | `arrow-left` |
| Forward | `fa-arrow-right` | `ArrowRightIcon` | `arrow-right` |
| Up | `fa-chevron-up` | `ChevronUpIcon` | `chevron-up` |
| Down | `fa-chevron-down` | `ChevronDownIcon` | `chevron-down` |
| External | `fa-arrow-up-right-from-square` | `ArrowTopRightOnSquareIcon` | `external-link` |

### Status
| Icon | Font Awesome | Heroicons | Lucide |
|------|-------------|-----------|--------|
| Success | `fa-check` | `CheckIcon` | `check` |
| Error | `fa-xmark` | `XMarkIcon` | `x` |
| Warning | `fa-triangle-exclamation` | `ExclamationTriangleIcon` | `alert-triangle` |
| Info | `fa-circle-info` | `InformationCircleIcon` | `info` |
| Loading | `fa-spinner` | `ArrowPathIcon` | `loader-2` |

### User/Social
| Icon | Font Awesome | Heroicons | Lucide |
|------|-------------|-----------|--------|
| User | `fa-user` | `UserIcon` | `user` |
| Users | `fa-users` | `UsersIcon` | `users` |
| Profile | `fa-user-circle` | `UserCircleIcon` | `user-circle` |
| Heart | `fa-heart` | `HeartIcon` | `heart` |
| Star | `fa-star` | `StarIcon` | `star` |
| Share | `fa-share-nodes` | `ShareIcon` | `share-2` |
| Comment | `fa-comment` | `ChatBubbleLeftIcon` | `message-circle` |

### File/Document
| Icon | Font Awesome | Heroicons | Lucide |
|------|-------------|-----------|--------|
| File | `fa-file` | `DocumentIcon` | `file` |
| Folder | `fa-folder` | `FolderIcon` | `folder` |
| Download | `fa-download` | `ArrowDownTrayIcon` | `download` |
| Upload | `fa-upload` | `ArrowUpTrayIcon` | `upload` |
| Attachment | `fa-paperclip` | `PaperClipIcon` | `paperclip` |
| Image | `fa-image` | `PhotoIcon` | `image` |

## Standard Sizes

```css
.icon-sm { width: 16px; height: 16px; }  /* Small UI */
.icon-md { width: 20px; height: 20px; }  /* Medium UI */
.icon-lg { width: 24px; height: 24px; }  /* Default */
.icon-xl { width: 32px; height: 32px; }  /* Large buttons */
.icon-2xl { width: 48px; height: 48px; } /* Hero icons */
```

## Accessibility Pattern

```html
<!-- Icon-only button -->
<button aria-label="Delete item">
  <i class="fa-solid fa-trash" aria-hidden="true"></i>
</button>

<!-- Icon with text -->
<button>
  <i class="fa-solid fa-save" aria-hidden="true"></i>
  <span>Save</span>
</button>
```

## Framework Examples

### React
```jsx
import { TrashIcon } from '@heroicons/react/24/outline'

<button aria-label="Delete">
  <TrashIcon className="h-5 w-5" />
</button>
```

### Vue
```vue
<button aria-label="Delete">
  <i class="fa-solid fa-trash" aria-hidden="true"></i>
</button>
```

### Svelte
```svelte
<script>
  import { Trash } from 'lucide-svelte';
</script>

<button aria-label="Delete">
  <Trash size={20} />
</button>
```

## iOS (Native)
```swift
Image(systemName: "trash")
  .font(.system(size: 20))
```

## Android (Native)
```kotlin
Icon(Icons.Default.Delete, contentDescription = "Delete")
```

## Remember

1. ✅ **Use icon libraries** - Font Awesome, Heroicons, Lucide, Material Symbols
2. ✅ **Choose ONE library per project**
3. ✅ **Include aria-label** for icon-only buttons
4. ✅ **Use aria-hidden="true"** for decorative icons
5. ❌ **NEVER generate SVG code** - massive token waste

**Full guide**: `.cursor/rules/15-icons-assets.mdc`

