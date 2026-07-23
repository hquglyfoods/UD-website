Ugly Donuts website upgrade v3: images + CLS + inKind (once-only popup)
========================================================================
WHAT CHANGED
1) uploads/: all images optimized (137.8MB -> 16.6MB, 88% smaller).
   42 photo-type PNGs converted to JPG; all references updated.
2) build-index.js: automatic build steps.
   - CLS: injects width/height into every <img>.
   - inKind: first-time visitors see the popup ONCE. After that it stays
     hidden (remembered in the visitor's browser). A footer link
     "inKind Rewards" (Brand column, under FAQ) reopens it anytime.
3) Regenerated pages with everything baked in.

HOW TO APPLY
1) Unzip into the repo root, overwriting existing files.
2) Commit and push. Netlify deploys automatically.
3) Test: open the site in a private/incognito window -> popup shows once.
   Reload -> no popup. Click footer "inKind Rewards" -> popup again.

OPTIONAL CLEANUP
DELETE-LIST-optional.txt lists 42 old .png files no longer referenced.
