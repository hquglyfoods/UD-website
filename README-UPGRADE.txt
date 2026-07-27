Ugly Donuts website upgrade v10 (light zip, no uploads folder)
===============================================================
THE ACTUAL CAUSE OF THE LOGIN TROUBLE

admin/config.yml had the site address written as
  site_url:    https://uglydonutswebsite.netlify.app
  display_url: https://uglydonutswebsite.netlify.app
  logo_url:    https://uglydonutswebsite.netlify.app/og-image.jpg

That is the address shown in the top right of the CMS, and where logout
sent you. The CMS was told it lives on the netlify.app address while it
actually runs on uglydonutsncorndogs.com, so sign-ins were made against
one address and checked against the other. Earlier attempts cleared
browser values, which was treating a symptom. This release fixes the
configuration itself.

THE FIXES
1) admin/config.yml now points at https://www.uglydonutsncorndogs.com.
2) netlify.toml sends every request for uglydonutswebsite.netlify.app to
   the custom domain with a permanent redirect. One address, one login,
   one set of pages in search results. The two addresses can no longer
   drift apart.
3) The sign-in check no longer guesses. It asks Identity whether the
   stored session can still be refreshed: refreshed successfully means
   signed in, refused means the session is cleared and the sign-in form
   appears. No more silent half-signed-in state.
4) README's broken admin address corrected.

ALSO IN THIS RELEASE (from earlier work)
- Identity script served from our own site, so a blocked third-party
  script can no longer break the login button.
- /admin has an email and password form built into the page. Your email
  is remembered; the cursor lands in the password box. The password is
  never stored by the site.
- "Email me a reset link" on the login screen.
- /admin/?relogin forces a fresh sign-in at any time.

HOW TO APPLY
Drag the uglydonutswebsite folder over your local repo (overwrite),
commit and push. Wait for the deploy, then open /admin/ and reload with
Ctrl+Shift+R.

HOW TO KNOW IT WORKED
The address in the top right of the CMS reads uglydonutsncorndogs.com,
not netlify.app. Logging out returns you to the same site, and saving a
Journal entry works.
