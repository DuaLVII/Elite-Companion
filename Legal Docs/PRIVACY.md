# Elite Companion · Privacy policy

*Last updated: 26 October 2026*

Elite Companion is a desktop app for Elite Dangerous that runs on your own PC. It has no accounts, no servers of its
own, no analytics, no tracking and no adverts. This page explains what it reads, what it keeps, and the few things it
can send to other services when you turn them on.

## What the app reads

- **Your Elite Dangerous journal and status files** (written by the game in your Saved Games folder): where you are,
  your ship, missions, cargo, scans and so on. They're read on your PC to fill in the dashboard.

## What the app keeps

Everything stays in files next to the app (or in `%AppData%\EliteCompanion` if the app's folder can't be written to),
on your PC only:

- `settings.json`: your layout, theme, language, hotkeys and other settings. If you use the Data Uploads module it
  also holds your EDSM commander name and API key.
- `addondata.json`: what addon modules remember between sessions.
- `hotspots.json`, `galactic-prices.json`, `designer-draft.json`, `startup-times.txt` and similar: things learnt from
  your journals, your unsaved addon design, and start-up timings for troubleshooting.

Delete these files (or the app's folder) and that data is gone. Nothing is kept anywhere else by the app.

## What the app sends, and only when you ask it to

| What | Sent to | When |
|---|---|---|
| Journal events (locations, markets, scans…) with your commander name as the uploader | [EDDN](https://github.com/EDCD/EDDN) (the community data network used by EDSM, Inara, Spansh and others) | Only while the **Data Uploads** module is on your dashboard with EDDN switched on |
| Journal events, your EDSM commander name and API key | [EDSM](https://www.edsm.net) | Only while the **Data Uploads** module is on your dashboard with EDSM switched on and your details filled in |
| A system or station name you look up | EDSM and / or [Spansh](https://spansh.co.uk) | When a module looks something up (stations, factions, hotspots, nearest wars…) |
| The app's version | GitHub | When it checks for app updates and when you open the addon gallery |
| What you're doing in game (if you turn it on) | Discord, through the Discord app on your PC | Only with **Discord rich presence** switched on in Settings; it shows on your Discord profile under your Discord privacy settings |

Those services handle what they receive under their own privacy policies. Addon modules can only ask the app to look
things up on EDSM or Spansh (and must say so); they can't read your files or reach anything else.

## Children

The app isn't aimed at children and doesn't knowingly collect anything from anyone.

## Changes

Any change to this policy is published here, with a new date at the top.

## Contact

Questions or concerns: open an issue at [github.com/DuaLVII/Elite-Companion](https://github.com/DuaLVII/Elite-Companion/issues).

*Elite Companion is a fan-made tool, not affiliated with or endorsed by Frontier Developments or Discord.*
