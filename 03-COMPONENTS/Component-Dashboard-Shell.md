# Component: Dashboard Shell

#component #core #layout

## File Path
`src/components/dashboard-shell.tsx` (366 lines)

## Purpose
Main authenticated layout wrapper. Sidebar + header + content area.

## Structure
- **Desktop**: Fixed sidebar (`lg:w-64`) with NavContent
- **Mobile**: Header with hamburger menu (Sheet-based) + bottom nav (4 items)
- **Mobile bottom nav**: Home, Templates, Documents, AI Coach + More

## NavContent Sections
1. Logo + "Advisor Intelligence" brand
2. **Main nav**: Home, AI Coach (blue gradient `from-blue-500 to-indigo-600`), Templates, Documents, Tutorials
3. **Action Plans** (with NEW badge)
4. **Admin Dashboard** link (if `isAdmin`)
5. **Secondary nav**: Favorites, History
6. **Footer**: Take Tour, Settings, Sign Out, Theme Toggle

## Side Effects
- Login tracking: POST to `/api/admin/track-login` (debounced 30 min)

## Includes
- [[Component-CommandPalette]] — Cmd+K search
- [[Component-SiteTour]] — Interactive tutorial
- [[Component-ChatWidget]] — Floating AI Coach

## Used On
Every dashboard page: [[Page-Dashboard]], [[Page-Toolkit]], [[Page-Documents]], [[Page-Chat]], [[Page-Settings]], [[Page-Favorites]], [[Page-History]], [[Page-Tutorials]], [[Page-Scenario-To-Plan]]

## Related Notes
- [[Architecture]] — Layout structure
- [[Design-System]] — Sidebar styling
