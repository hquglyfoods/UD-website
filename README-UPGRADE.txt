Ugly Donuts website upgrade v8 (light zip, no uploads folder)
==============================================================
Everything from v7.1, plus the survey page now scales with the brand.

1) STORES COME FROM THE CMS
   The survey no longer has stores hardcoded. The build generates
   content/locations/_stores.json from your Store Locations entries,
   and the survey reads that. Open a new store in the CMS and it
   appears in the survey automatically. No code changes needed.
   New CMS field: Store Locations > Google Place ID.
   (The 4 existing stores already have theirs filled in.)
   A store with no Place ID is skipped safely, and the QR page tells
   you which ones are missing it.

2) THE LIST ADAPTS AS YOU GROW
   6 stores or fewer: simple cards, exactly as it looks today.
   7 or more: stores are grouped by state and a search box appears
   (matches store name, city, state). Verified with a simulated
   20-store, 4-state setup.

3) QR CODES INSIDE THE CMS
   A new "Survey QR Codes" link appears in the CMS sidebar. It opens
   /qr.html, which shows a QR code for every store you have entered,
   with a Download PNG button for each. Open a store, get its QR.
   The QR library is vendored in js/ (MIT, no dependencies, no CDN).
   Verified by decoding a generated QR back to its URL.

HOW TO APPLY
Drag the uglydonutswebsite folder over your local repo (overwrite),
commit and push. Nothing to delete.

WHEN YOU ADD A STORE LATER
1) CMS > Store Locations > New. Fill in the Google Place ID.
2) Publish. After the deploy finishes, the store shows up in the
   survey, and its QR is waiting under Survey QR Codes.
