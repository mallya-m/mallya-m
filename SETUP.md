# Setup

## Push it (same pattern as before — new folder this time)

```powershell
cd path\to\this\unzipped\profile
git init
git remote add origin https://github.com/mallya-m/mallya-m.git
git add .
git commit -m "reliable stats, real skill icons"
git branch -M main
git push -u origin main --force
```

`--force` because this folder has no shared history with what's already on
GitHub — it fully replaces it, which is what you want.

## Turn on both Actions (one-time, ~1 minute)

Go to your repo's **Actions** tab. You'll see two workflows:

1. **Generate Snake** → click it → **Run workflow** → confirm
   - Creates real `assets/snake-dark.svg` / `snake-light.svg` from your
     actual contribution graph.
2. **Generate Profile Cards** → click it → **Run workflow** → confirm
   - Creates a `profile-summary-card-output/github_dark/` folder with
     `profile-details.svg` and `repos-per-language.svg` — your real stats,
     as committed files, not a live call to a third-party server.

Wait ~30–60 seconds after each, refresh the Actions tab to confirm they show
a green checkmark, then go to `github.com/mallya-m` and hard refresh
(Ctrl+Shift+R).

Both Actions re-run automatically after this (snake every 6 hours, cards
once a day) — nothing more to do.

## Why this approach instead of the badge URLs from before

The public `github-readme-stats.vercel.app` service that generates stats
on-the-fly every time someone loads your profile has been unreliable for
months — it's a known, widely-reported issue on their GitHub repo, not
something wrong with your setup. Generating the cards once via Action and
committing the actual SVG file removes that dependency entirely: your
profile stops relying on someone else's server being up at the moment
someone visits it.

## If a card still looks broken after running the Action

Open the direct file path in your repo (Code tab → navigate to
`profile-summary-card-output/github_dark/`) to confirm the files exist. If
they're there but not showing in the README, it's almost always a GitHub
image cache — hard refresh, or wait a few minutes.
