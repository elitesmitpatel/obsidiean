# PWA

## What it does
Provides installable app shell behavior with manifest, service worker, icons, and app-shell precaching.

## Integration
[[PWA Integration]]

## Important boundary
Downloaded note content is NOT precached as static service-worker assets. Offline note content comes from IndexedDB.

## Change Impact
- Vite/PWA build configuration
- manifest
- service worker generation
- hosting deployment
- installability
- offline expectations
- browser QA
