Ugly Donuts website upgrade v11: new CMS login
================================================
The login mechanism has been replaced rather than patched.

BEFORE: Decap CMS -> Netlify Identity -> Git Gateway -> GitHub.
Two brokers sat between the editor and the repository. Both held
credentials that expire, and when either one went stale the CMS looked
signed in while every save failed ("Requires authentication",
"API rate limit exceeded").

NOW: Decap CMS -> GitHub. One hop, no brokers.
Sign-in is a single "Login with GitHub" button. Nothing to invite,
nothing to expire, no password stored anywhere. Whoever has write access
to the repository can edit the site.

WHAT WAS REMOVED
- Netlify Identity widget (deleted, including the copy in js/)
- Git Gateway (no longer referenced anywhere)
- The custom email/password form and every workaround added around it
- Identity invite-token scripts that were sitting on 21 public pages

SETUP: three steps, once
1) Register a GitHub OAuth App
   https://github.com/settings/developers -> New OAuth App
     Application name:          Ugly Donuts CMS
     Homepage URL:              https://www.uglydonutsncorndogs.com
     Authorization callback URL: https://api.netlify.com/auth/done
   Create it, copy the Client ID, then "Generate a new client secret"
   and copy that too.

2) Give the keys to Netlify
   Netlify -> your site -> Site configuration -> Access control -> OAuth
   -> Install provider -> GitHub -> paste Client ID and Client Secret
   -> Save.

3) Deploy this zip, then open /admin and click "Login with GitHub".

ADDING AN EDITOR LATER
GitHub -> repository -> Settings -> Collaborators -> add their GitHub
account with write access. They then sign in at /admin the same way.
Deborah will need a GitHub account for this.

OPTIONAL CLEANUP
Netlify Identity and Git Gateway can now be turned off in the Netlify
dashboard. Nothing on the site uses them.
