Ugly Donuts website upgrade v7.1 (light zip, no uploads folder)
================================================================
1) FIXED: stretched nav logo across the site (CLS work now uses
   aspect-ratio styles instead of width/height attributes, and
   auto-migrates every page).
2) REBUILT: /review uses the exact same shell as the main site.
   Verified pixel-for-pixel vs contact.html: logo 95x95, nav 1280x147,
   CTA, footer height, nav background and position all identical.
3) Mobile verified at 320 / 360 / 390 / 430 px: no horizontal scroll,
   no text clipping, no overflow. Star rating touch targets enlarged
   to 46x46 px (were 31x34, below the comfortable tap size).
4) Nav: "Share Your Visit" in the More dropdown on every page.

HOW TO APPLY
Drag the uglydonutswebsite folder over your local repo (overwrite),
commit and push. Nothing to delete.
