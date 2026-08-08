# App Shell Module

**Location:** `src/features/app-shell/`

## Responsibility
Provide authenticated layout, header/content outlet, bottom navigation, scroll restoration, and safe-area support.

## Files
- `app-layout.tsx`
- `bottom-navigation.tsx`

## Routes
Wraps authenticated routes through [[Router]].

## Screens
[[Home Screen]], [[Search Screen]], [[Bookmarks Screen]], [[Profile Screen]], [[Downloads Screen]].

## Change Impact
Changing layout affects every authenticated screen. Changing bottom-navigation items affects route discoverability, navigation tests, and the documented four-item navigation contract. Changing safe-area/scroll behavior affects mobile UX across all protected pages.
