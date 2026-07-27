Ugly Donuts website upgrade v9.3 (light zip, no uploads folder)
================================================================
Everything from v8, plus a full fix for the CMS login trouble.

THE THREE THINGS THAT WERE BREAKING LOGIN
1) The login popup came from identity.netlify.com. Phones and content
   blockers can cut off that third-party script, and then the button
   does nothing at all.
2) An expired session stayed in the browser, so the CMS looked signed
   in while every GitHub request went out unauthenticated. That is what
   produced "API rate limit exceeded" and "Requires authentication".
3) The widget had remembered the wrong site address
   (uglydonutswebsite.netlify.app) while the CMS runs on
   uglydonutsncorndogs.com. Login succeeded against the wrong site, so
   the CMS never accepted it and the dialog kept coming back.

WHAT CHANGED
- The Identity script is served from our own site (js/).
- /admin has a plain email and password form built into the page.
  Your email is remembered and filled in; the cursor lands in the
  password box. The password is never stored by the site.
- "Email me a reset link" is on the login screen.
- A remembered site address that does not match the current domain is
  cleared automatically, along with the bad session it created.
- Sessions expired for more than 7 days are cleared automatically.
- If the CMS shows its own login screen, our sign-in form appears over
  it, so there is always a way in.
- /admin/?relogin always forces a fresh sign-in. Worth bookmarking.

HOW TO APPLY
Drag the uglydonutswebsite folder over your local repo (overwrite),
commit and push. Nothing to delete. Wait for the Netlify deploy to
finish, then open /admin/?relogin and sign in.
