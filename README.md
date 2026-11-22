# Palma Bay — Top-Down Open-World Crime Game

An entry for the make.fun bounty "Make GTA 6" ($1,666). An original game: its own
city, characters, vehicles, names, story and art. No Rockstar Games assets, names,
characters or map, and no network requests — the game is static files under `game/`.

## Play it

Serve `game/` with any static server, or run `node serve.ts` and open
http://localhost:8080 in a desktop browser. No build step, no server needed beyond
that. Progress (money, missions completed) saves in `localStorage`.

## Controls

- **WASD** — move on foot / drive
- **Shift** — sprint
- **E** — enter / exit a car
- **Mouse click or Space** — shoot toward the mouse
- **P or Esc** — pause
- **R** — restart after Wasted / Busted / Story Complete

## What is in the game

- A 2400×1800 city with a road grid, buildings, parks, traffic cars and pedestrians
- On foot and by car: enter/exit cars, drive, traffic that follows the roads
- Car theft: stealing a moving traffic car raises your wanted level; parked cars are free to take
- Wanted level 0–5 stars: police cars chase and ram you, officers on foot chase, shoot and arrest you
- Combat: shoot, police return fire, pedestrians flee, fallen pedestrians drop $20
- HUD: health, money, wanted stars, mission objective, driving/on-foot state, minimap
- Start screen, pause, Wasted / Busted lose states, Story Complete win state

## Missions (story: Marco owes a debt in Palma Bay)

1. **First Wheels** — steal a car, drive it to Dana's Garage. Reward $250.
2. **The Pickup** — drive to the north pickup point, bring the package back to Dana. Reward $500.
3. **The Getaway** — grab the cash at the bank (wanted level jumps to 3), escape to the safehouse. Reward $800.

## Screenshots

`screenshots/` holds 4 real renders of the game in a desktop browser, staged with
`?shot=start|play|chase|end` (see `shots.json`): the start screen, driving through
the city, a police chase at wanted level 3, and the Story Complete screen.

## Layout

- `main.ts` — the entry program: copies `game/` and `screenshots/` to `/output` and writes `dossier.json` with `buildDossier` from `vendor/makefun-game.ts`
- `game/index.html` — the whole game, single self-contained file
- `vendor/makefun-game.ts` — the kit's library, unchanged
- `serve.ts` — tiny static server for local testing
- `shots.json` — the screenshot scenes and their `?shot=` queries
