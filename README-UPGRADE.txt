Ugly Donuts website upgrade v5
================================
Everything from v4 (images, CLS, inKind once-only popup, security
hardening) PLUS the new review funnel:

NEW: /review survey page
- Step 1: pick your store (4 cards; ?store=xxx preselects via QR)
- Step 2: survey questions + email for the monthly $50 gift card draw
  * Questions are FULLY EDITABLE in /admin > Survey > Survey Questions.
    Add as many as you want; each can be short answer, long answer,
    multiple choice, star rating, or yes/no.
- Step 3: thank-you + "Copy my words & open Google" button that copies
  their written feedback and opens that store's Google review dialog.
- Entries are saved to Netlify Forms (form name: "survey") for the
  monthly drawing and internal feedback.

HOW TO APPLY
1) Drag the uglydonutswebsite folder over your local repo (overwrite),
   delete files in DELETE-LIST.txt, commit and push.
2) After the first deploy with this form, check Netlify > Forms:
   a form named "survey" should appear. Entries collect there.
3) Print the QR codes (separate download) and place them at pickup
   counters and tables. Each QR opens /review with that store
   preselected.
