---
name: mba-build-dashboard-page
description: Generate a professional dashboard page with data visualization and controls
---

# MBA Build Dashboard Page

Generate a complete, data-dense dashboard page with proper layout, realistic data, and interactive components.

## Arguments

- `dashboard_name` (required): Name of the dashboard (e.g., "Sales Analytics Dashboard", "Admin Panel")
- `layout` (optional): sidebar-left|sidebar-right|topbar-only - default: sidebar-left
- `widgets` (optional): Comma-separated list (e.g., "metrics,chart,table,activity") - default: "metrics,chart,table"
- `theme` (optional): enterprise|neutral|editorial|playful - default: enterprise
- `data_type` (optional): sales|analytics|admin|monitoring - default: analytics
- `platform` (optional): web|desktop - default: web

## Instructions

1. **Review Dashboard Patterns**:
   - Read `.cursor/rules/60-pages-templates.mdc`
   - Reference `.mba-template/patterns/dashboard-layouts.md`
   - Check `.cursor/rules/50-components.mdc` for data table patterns

2. **Generate Page Structure**:
   ```html
   <!DOCTYPE html>
   <html lang="en">
   <head>
     <meta charset="UTF-8">
     <meta name="viewport" content="width=device-width, initial-scale=1.0">
     <title>{dashboard_name}</title>
   </head>
   <body>
     <div class="dashboard-layout">
       <header class="dashboard-header">
         <!-- Logo, search, notifications, profile -->
       </header>
       
       <aside class="dashboard-sidebar">
         <!-- Navigation -->
       </aside>
       
       <main class="dashboard-main">
         <div class="page-header">
           <!-- Page title, actions, filters -->
         </div>
         
         <div class="metrics-grid">
           <!-- KPI cards -->
         </div>
         
         <div class="dashboard-content">
           <!-- Charts, tables, widgets -->
         </div>
       </main>
     </div>
   </body>
   </html>
   ```

3. **Header Component** (56-64px height, sticky):
   - **Logo/Brand**: Left side
   - **Search**: Center or left (optional)
   - **Actions**: Right side
     - Notifications icon (with badge if unread)
     - Settings icon
     - Profile avatar + dropdown

4. **Sidebar Navigation** (240-280px, collapsible):
   - **Logo**: Top
   - **Navigation items**:
     - Icon (20-24px) + Label
     - Active indicator (left border or background)
     - Hover state
   - **Sections**: Grouped with headers
   - **Collapse button**: Bottom or top-right
   - **Collapsed state**: 56-64px width, icons only

5. **Page Header**:
   - **Title** (H1): Dashboard name
   - **Breadcrumbs**: Optional navigation trail
   - **Actions**: Primary actions (Export, Share, etc.)
   - **Filters**: Date range, status, category
   - **Tabs**: If multiple views

6. **Metrics Cards** (2-4 columns):
   ```html
   <div class="metric-card">
     <div class="metric-label">Total Revenue</div>
     <div class="metric-value">$1,234,567</div>
     <div class="metric-change positive">+12.5%</div>
     <div class="metric-period">vs last month</div>
   </div>
   ```
   
   **Realistic Data Examples**:
   - Revenue: $1,234,567 (not $1,000,000)
   - Users: 12,345 (not 10,000)
   - Growth: +12.5% (not +10%)
   - Conversion: 3.42% (not 3%)

7. **Chart Widget**:
   - **Title**: Chart name
   - **Legend**: Color-coded
   - **Axes**: Labeled with units
   - **Tooltip**: On hover
   - **Time period**: Selector (7d, 30d, 90d, 1y)
   - **Realistic data**: Varied, not perfect lines

8. **Data Table**:
   - **Headers**: Sortable columns (with icon)
   - **Rows**: 10-20 visible, pagination
   - **Columns**: 4-8 columns
   - **Row hover**: Subtle background
   - **Actions**: Per row (view, edit, delete)
   - **Selection**: Checkboxes (optional)
   - **Empty state**: "No data available"
   - **Loading state**: Skeleton or spinner

   **Realistic Data**:
   ```
   | Name          | Email                | Status  | Revenue   | Date       |
   |---------------|----------------------|---------|-----------|------------|
   | Sarah Johnson | sarah.j@acme.com     | Active  | $12,345   | 2024-01-15 |
   | Michael Chen  | m.chen@techcorp.io   | Pending | $8,234    | 2024-01-14 |
   | Emma Williams | emma.w@startup.co    | Active  | $23,456   | 2024-01-13 |
   ```

9. **Activity Feed** (optional):
   - **Avatar**: User photo (32-40px)
   - **Action**: "Sarah Johnson created a new report"
   - **Timestamp**: "2 hours ago"
   - **Icon**: Action type indicator

10. **Filters & Search**:
    - **Search bar**: Prominent, with icon
    - **Date range**: Picker or presets
    - **Status filter**: Dropdown or chips
    - **Category filter**: Multi-select
    - **Apply/Clear**: Action buttons

11. **Responsive Behavior**:
    - **Mobile** (< 640px):
      - Sidebar: Hidden, hamburger menu
      - Metrics: Single column
      - Table: Card-based layout
      - Charts: Full width, scrollable
    - **Tablet** (640-1023px):
      - Sidebar: Collapsible
      - Metrics: 2 columns
      - Table: Horizontal scroll if needed
    - **Desktop** (1024px+):
      - Full layout
      - Metrics: 3-4 columns
      - Table: Full width

12. **Empty States**:
    - "No data available"
    - "No results found"
    - "Start by adding your first item"
    - Icon + message + CTA

13. **Loading States**:
    - Skeleton screens for cards
    - Spinner for tables
    - Progress bar for long operations

14. **Error States**:
    - "Failed to load data"
    - "Connection error"
    - Retry button

## Common Dashboard Types

### Sales Dashboard
- Metrics: Revenue, Orders, Conversion Rate, AOV
- Charts: Revenue over time, Top products
- Table: Recent orders
- Filters: Date range, status, sales rep

### Analytics Dashboard
- Metrics: Users, Sessions, Bounce Rate, Avg Duration
- Charts: Traffic over time, Top pages
- Table: Top referrers
- Filters: Date range, device, country

### Admin Panel
- Metrics: Total Users, Active Sessions, Storage Used
- Charts: User growth, Activity heatmap
- Table: Recent users, System logs
- Actions: User management, Settings

### Monitoring Dashboard
- Metrics: Uptime, Response Time, Error Rate, CPU Usage
- Charts: Performance over time, Error trends
- Table: Recent incidents
- Alerts: Critical issues

## Output Files

1. `pages/dashboard.html` - Complete dashboard page
2. `pages/dashboard.css` - Page-specific styles
3. `components/metric-card.html` - Reusable metric card
4. `components/data-table.html` - Reusable data table
5. `docs/dashboard-guide.md` - Documentation

## Quality Checks

- [ ] Semantic HTML structure
- [ ] Sidebar navigation functional
- [ ] Metrics cards with realistic data
- [ ] Data table with sortable columns
- [ ] Charts with proper labels
- [ ] Filters/search implemented
- [ ] Responsive layout (mobile, tablet, desktop)
- [ ] Empty states designed
- [ ] Loading states included
- [ ] Error states handled
- [ ] WCAG AA contrast
- [ ] Keyboard navigation
- [ ] Focus indicators
- [ ] No Lorem Ipsum
- [ ] Realistic, varied data

## Example Usage

```
/mba-build-dashboard-page dashboard_name="Sales Analytics Dashboard" layout="sidebar-left" widgets="metrics,chart,table,activity" theme="enterprise" data_type="sales"
```

This will generate a complete sales analytics dashboard with enterprise theme, sidebar navigation, and all specified widgets.

## Anti-Patterns to Avoid

Reference `.cursor/rules/80-anti-ai-patterns.mdc`:
- No perfect round numbers (use $1,234.56 not $1,000)
- No all-same dates (vary timestamps)
- No missing empty states
- No missing loading states
- No missing error states
- No inconsistent spacing
- No low contrast text
- No tiny click targets
- No generic "User 1", "User 2" names
- No Lorem Ipsum text

## Accessibility Requirements

- Semantic landmarks (header, nav, main, aside)
- Proper heading hierarchy
- ARIA labels for icons
- Keyboard navigation for all interactions
- Focus indicators on all interactive elements
- Screen reader support for charts (data table fallback)
- Color not sole indicator (use icons too)
- WCAG AA contrast minimum

