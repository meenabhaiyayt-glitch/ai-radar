# AI Radar — Deploy & Update Guide

## Deploy on Vercel (recommended)
1. Create a GitHub repo, upload all files in this folder.
2. vercel.com -> Add New -> Project -> import the repo -> Framework: "Other" -> Deploy.
3. Every time you push a change to GitHub, Vercel redeploys automatically.

## Deploy on Netlify (fastest, no GitHub)
1. Go to app.netlify.com/drop
2. Drag this whole folder onto the page. Live in ~30 seconds.
(For auto-deploys later, connect the same GitHub repo in Netlify.)

## How to update AI tools / models / offers
All content lives in JavaScript data arrays inside index.html
(search for the arrays of models, tools, new apps, offers, benchmarks).
Edit the entry, commit to GitHub -> site updates automatically.

Option A (easiest): ask Hark "update AI Radar with this week's releases",
download the new files, push to GitHub.

Option B (automatic): later, move the arrays into a data.json and add a
GitHub Action on a weekly cron that pulls public sources, e.g.
- OpenRouter models list: https://openrouter.ai/api/v1/models
- Hugging Face trending models: https://huggingface.co/api/models?sort=trendingScore
and commits the new data.json. Vercel/Netlify redeploy on each commit.

Benchmarks (Artificial Analysis, LMArena, Vals) should still be checked by hand
before publishing, since they change weekly and have no free open feed for all.

## New settings (CONFIG at top of the main script in index.html)
- ADSENSE_CLIENT: your AdSense publisher id, e.g. "ca-pub-1234567890123456". Leave "" to hide ads.
- ADSENSE_SLOT: your ad unit slot id from AdSense.
- FORM_ENDPOINT: a Formspree (formspree.io) form URL for tool suggestions. Empty = opens email to SUGGEST_EMAIL.
- After AdSense approval, add a file ads.txt in this folder with:
  google.com, pub-XXXXXXXXXXXXXXXX, DIRECT, f08c47fec0942fa0
- Upvotes/ratings are saved per device (localStorage); global totals need a backend later.
