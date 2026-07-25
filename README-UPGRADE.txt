Ugly Donuts website upgrade v4
================================
Includes everything from v3 (image optimization 88%, CLS, inKind
once-only popup + footer link) PLUS security hardening:

1) URL validation in both markdown renderers (build + runtime).
   javascript:/data: and quote-injection URLs are neutralized.
   Verified with live payload tests (8/8 build, 6/6 runtime pass).
2) Decap CMS pinned to exact version 3.15.1 (was ^3.0.0 floating).
3) Netlify Identity widget removed from all 10 public pages,
   replaced by a tiny invite-token redirect (admin keeps the widget).
   Less third-party JS for every visitor.
4) /order redirect now points to the real Toast ordering page and the
   junk utm_source=undefined parameters are gone.
5) Cache policy fixed: hashed images 1y immutable, named images and
   uploads 1 day (logo swaps now show up within a day, not a year).
   /admin is noindex + no-store.
6) Duplicate root config.yml removed (admin/config.yml is the source
   of truth). See DELETE-LIST.txt: delete config.yml from the repo.
7) Form fields now have sensible maxlength limits on all 4 forms.

HOW TO APPLY
1) Drag the uglydonutswebsite folder over your local repo folder
   (merge/overwrite), delete the files in DELETE-LIST.txt,
   commit and push.
2) In the Netlify dashboard, verify: Identity > Registration is
   INVITE ONLY, and remove any unknown invited emails.
