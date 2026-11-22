# Palma Bay

An original, top-down 2D open-world crime game in the make.fun `gta6-01` kit layout. Explore a 2400 × 1800 coastal city on foot or in a stolen car, complete three jobs, and survive the police response. The complete game is in `game/index.html`.

All characters, names, city details, and canvas art are original. There are no Rockstar assets, external assets, dependencies, or game network requests.

## Play

Use a recent Node.js version with native TypeScript support (Node 22.18+), then run:

```powershell
node serve.ts
```

Open <http://localhost:8080> in a desktop browser. Choose a new game or continue saved progress. The static HTML can also run directly in a browser; a local server gives `localStorage` a consistent origin. To choose another port, use `node serve.ts --port 8081`.

## Controls

| Control | Action |
| --- | --- |
| WASD | Move on foot or drive |
| Shift | Sprint on foot |
| E | Enter or exit a nearby car |
| Mouse | Aim |
| Left mouse button / Space | Shoot toward the mouse |
| P / Esc | Pause or resume |
| R | Retry the current job after Wasted or Busted |

The HUD shows health, money, up to five wanted stars, the active mission, and a minimap. Follow the mission marker. Stealing moving traffic raises the wanted level. Police cars pursue and ram; officers chase on foot, shoot, and arrest. Stay alive and evade the response to finish the story. Health depletion causes **Wasted**; capture causes **Busted**. Finishing all three jobs reaches **Story Complete**.

## Story jobs

1. Steal a car and deliver it to **Dana's Garage** — **$250**.
2. Collect the package and bring it back — **$500**.
3. Rob the bank and escape to the safehouse — **$800**.

Progress saves in browser `localStorage`. Keep the same browser and URL to continue. Browser privacy settings may prevent saving; the game remains playable for the current session.

## Build the kit output

`main.ts` uses the starter kit's original packaging logic and `buildDossier` limits. It copies `game/` and `screenshots/` to `/output` and writes `dossier.json`. A successful build does not publish or submit anything.

PowerShell:

```powershell
$env:MAKEFUN_OUTPUT_DIR = 'out'
node main.ts
```

POSIX shell:

```sh
MAKEFUN_OUTPUT_DIR=out node main.ts
```

The result is `out/game/index.html`, four images under `out/screenshots/`, and `out/dossier.json`. Omit `MAKEFUN_OUTPUT_DIR` to use `/output`.

## Repository layout

| Path | Purpose |
| --- | --- |
| `game/index.html` | Single-file game, interface, original art, simulation, and saving |
| `main.ts` | Starter-compatible copy and dossier build entry |
| `serve.ts` | Local development server serving only `game/` |
| `vendor/makefun-game.ts` | Byte-for-byte copy of the starter kit library |
| `shots.json` | Start, play, chase, and ending screenshot scene queries |
| `screenshots/` | Four existing real screenshots, preserved unchanged |

The existing screenshot files are retained as supplied. `?shot=start`, `?shot=play`, `?shot=chase`, and `?shot=end` select the corresponding preview scenes; `seed=1` selects the repeatable scene seed.
