Ugly Donuts website upgrade v9.1 (light zip, no uploads folder)
================================================================
Everything from v8, plus the CMS login fix.

WHY LOGIN KEPT FAILING
The login popup came from a script hosted on identity.netlify.com.
When a phone blocks that third-party script, the button does nothing.
And an old expired session stays in the browser, so the CMS looks
signed in while every GitHub request goes out unauthenticated. That is
what produced the "API rate limit exceeded" message.

WHAT CHANGED
1) The Identity script is now served from our own site (js/), so there
   is no third-party script to block.
2) /admin has a plain email and password form built into the page.
   No popup. Same on phone and desktop.
3) Your email is remembered after the first sign-in and filled in
   automatically, with the cursor already in the password box. The
   password itself is never stored by the site; the phone's own
   password manager can fill it (autocomplete is set up for that).
4) "Email me a reset link" is on the login screen if the password is
   forgotten.
5) A session expired for more than 7 days is cleared automatically, so
   you get the login form instead of silent errors.
6) /admin/?relogin always forces a fresh sign-in. Worth bookmarking.

HOW TO APPLY
Drag the uglydonutswebsite folder over your local repo (overwrite),
commit and push. Nothing to delete.

AFTER DEPLOY
Open /admin/?relogin, sign in once with email and password. From then
on only the password is needed.
