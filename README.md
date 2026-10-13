# Elite Companion

A live companion display for **Elite Dangerous**, built with C# / WPF (.NET 10).
It reads the game's own journal files — no memory hacking, no API keys — so it's fully allowed by Frontier.

Run it on a second monitor, or switch to **overlay mode** to float it on top of the game.

## What it shows

| Panel | Data |
|---|---|
| Commander | Name, balance, legal state, game mode, **ranks with progress** (combat, trade, exploration, plus mercenary / exobiology / navy ranks once started) |
| Ship | Ship type & name, fuel & hull bars, cargo, max jump range, power distributor pips |
| Status | Shields, gear, hardpoints, scoop, fuel scooping, mass lock, FSD charging, silent running, **low fuel / heat / danger / interdiction** warnings |
| Location | System, station, body, economy, security, population, planetary lat/long + heading + altitude |
| Navigation | Next jump, route destination, jumps remaining, and **every system left on the route** with its star class — non-scoopable stars flagged, plus "next fuel star in N jumps" |
| **Missions** | Every active mission: destination system & station, objective (cargo, passengers, assassination target, massacre kills *5/12* with a progress bar), reward, time left. Sorted so the ones for **this station / this system / on your route** come first |
| **Target** | The ship you've locked: pilot, rank, legal status, bounty, faction, targeted subsystem, shield & hull — flagged if it's a **mission target** |
| **Cargo** | What's in the hold (mission cargo ✉ and stolen goods marked) |
| **Mining** | Tons refined per material this session with tons/hour, the last prospector result (every material's %, content level, ★ motherlodes), limpets left (red under 5), free hold space, prospectors/collectors fired. Alerts on a motherlode or a rock with 30%+ of a material |
| This session | Jumps, distance, profit, kills, bounties, missions, bodies scanned, estimated exploration value |
| System bodies | Everything scanned in the current system, most valuable first (★ for Earth-likes, water/ammonia worlds, terraformables). Also filled from EDSM when you arrive or start the game in a system (marked `· EDSM`); your own scans replace those entries |
| Header | Big at-a-glance strip: system name, commander, station/body, flight mode, ship, fuel & hull, clock and session time |
| Factions | Every minor faction in the system: influence (bar + %), change since yesterday, states (active / pending / recovering), government, happiness, **your reputation**, the controlling faction (♛), wars and elections, Powerplay, and an influence-history graph |
| Ship's log | A running feed of jumps, docking, scans, bounties, trades, missions, interdictions, player messages |
| And More | Any data that can be seen from the ED Journals I have tried to add |
| Addon Modules | Custom modules can be made currently using JS but may change in future... |

### Notifications

Notifications stack along the top of the window, most urgent first (red danger, deep-orange warning, orange info).
Each one loops a **lighter-orange burst that explodes from the centre to the edges** and fades back to the normal colour.

Some stay up **for as long as the thing is true** and disappear by themselves when it stops:

- **Jumping:** the next star's name, class and whether it's scoopable, plus how many jumps follow. Stays through the whole hyperspace jump, then switches to "ARRIVED".
- **FSD charging**, **hardpoints deployed**, **cargo scoop deployed**, **landing gear down** (in flight), **silent running**, **fuel scooping** (with live fuel %), **mass locked** (off by default)
- **Low fuel**, **overheating**, **being interdicted**, **shields down**

Others pop up for a few seconds: **under attack**, **hull damage**, **ship destroyed**, **docking granted / denied / timed out**,
**supercruise entry and drop** (off by default), escaped interdiction, mission updates and expiry warnings, mission targets, valuable bodies, motherlodes and rich rocks.

**ALERTS** in the title bar opens the notification settings. Switch each type on or off, turn the flashing animation off,
press **TEST** to preview, or **DEFAULTS** to undo your changes. Choices are saved. Esc closes the panel.

The Missions, Target, Cargo, Mining, Flight telemetry and Suit modules always keep their place on the dashboard; with nothing to show they sit blank with a short note (e.g. *No target locked*) and fill in as soon as there's data.

*Why no refinery bins?* The game never writes the refinery's partial-ton bins to the journal or status files, so no
companion app can show them. The Mining panel uses what the game does log: each ton as it's refined, prospector results and limpet counts.

### Where the mission details come from

The game only writes a mission's full details (destination, target, kill count) once, when you accept it.
So on startup the app reads back through your last 35 days of journals to rebuild your active missions, including
kill progress for massacre missions, then uses the login mission list to drop anything that's finished.
Missions accepted longer ago than that still appear, but without a destination.
