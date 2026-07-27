Ugly Donuts website upgrade v9.4 (light zip, no uploads folder)
================================================================
Fixes the CMS login for good.

WHAT WAS STILL WRONG IN v9.3
The cleanup code that removes the wrong remembered site address ran at
the bottom of the page, after the Identity widget had already started
and read the value. The widget then wrote it straight back, so the
top right of the CMS kept showing uglydonutswebsite.netlify.app and
logins kept bouncing. In v9.4 that cleanup runs first, before the
widget loads, so the value is gone before anything can read it.

EVERYTHING IN THIS RELEASE
- Identity script served from our own site (js/), not a third party.
- /admin has a plain email and password form built into the page.
  Your email is remembered; the cursor lands in the password box.
  The password is never stored by the site.
- "Email me a reset link" on the login screen.
- A remembered site address from another domain is cleared before the
  widget starts, along with the bad session it created.
- Sessions expired for more than 7 days are cleared automatically.
- If the CMS shows its own login screen, our form appears over it.
- /admin/?relogin forces a fresh sign-in at any time.

HOW TO APPLY
Drag the uglydonutswebsite folder over your local repo (overwrite),
commit and push. Wait for the deploy to finish, then open
/admin/?relogin and sign in. If the browser still shows the old page,
reload with Ctrl+Shift+R.

HOW TO KNOW IT WORKED
The site address in the top right of the CMS disappears. That means
the CMS is using the site it is actually running on.
