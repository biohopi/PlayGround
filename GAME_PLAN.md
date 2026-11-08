# FIELD//ZERO — Complete Game Build Plan

## Product brief
Build a polished, landscape-first, browser-based 3D tactical shooter inspired by the pacing and interface conventions of modern mobile battle royale games. This is an original offline prototype, not a PUBG asset or trademark replica. The online tab is a clearly marked future integration point; no networking or matchmaking is claimed. Desktop keyboard/mouse and mobile multi-touch are both first-class. Prefer a runnable, attractive, fully interactive slice over empty promises of PC-game scale.

## Requirements captured
- Real-time 3D first-person shooter, full-screen option, landscape-oriented presentation and responsive layout.
- Launch/lobby tab with Play/Offline, Online, Settings and customizable/draggable HUD layout.
- Offline setup with Start Match and bot count controls. Bot count starts at zero; both teams can be configured independently with plus/minus controls.
- In-match pause screen with return-to-lobby and HUD layout customization.
- Match HUD: fixed (non-dynamic) movement joystick, fast default sprint, aim/scope, fire, jump, crouch, heal, backpack, two primary weapon slots and swap.
- Efficient simultaneous touch input; keyboard/mouse controls on desktop.
- Minimap and player-facing/FOV indicator with player positions.
- A world with varied loot, layered 1–3 story buildings, navigable cover and responsive target actors.
- Backpack with effectively unlimited capacity, loot interaction and functional weapons/healing.
- Strong visual hierarchy, detailed world materials/lighting/sky, polished interface, and maintainable performance.
- A complete step-by-step plan and implementation process recorded in this file.

## Assumptions and scope
- Single-player offline sandbox/match loop; “Online” is a future-service placeholder, because no server/authentication/matchmaking requirements or backend are supplied.
- Original fictional locations, weapon names, UI, and generated geometry/materials; no proprietary game assets are copied.
- Procedural low-poly/high-detail-by-material environment keeps first load fast and avoids unreliable third-party asset downloads. Three.js is the real-time renderer.
- Bot count defaults to zero. When enabled, bots are split evenly across two teams as much as possible and are simple local sparring actors, not networked players.
- Web prototype has no claim to the content scale or fidelity of a commercial PC title; prioritize a complete performant playable vertical slice.

## Phased plan and acceptance checks

### 1. Project foundation and quality bar — COMPLETE
- Inspect workspace and choose a minimal browser project architecture.
- Document requirements, scope, user controls, phases and pass conditions here.
- Pass: a newcomer can identify the scope, steps and intentional limitations before implementation.

### 2. Game shell, responsive launch UI and settings
- Create runnable app, full-screen landscape presentation and premium game identity.
- Implement launch tabs for Offline, Online placeholder, Settings and layout editing.
- Add offline setup, independent team bot counters (0 default), and start-match flow.
- Pass: all menu tabs/buttons are usable on desktop and narrow/mobile screens; bot controls clamp safely.

### 3. 3D battlefield and player controller
- Build a Three.js scene with terrain, sky/fog, lighting, roads, vegetation, cover, loot, and distinct 1/2/3-story buildings.
- Implement first-person camera, sprint movement, collision, mouse look, pointer lock and mobile fixed joystick/look gestures.
- Pass: movement feels responsive; camera remains grounded; scenery is readable and visible from playable areas.

### 4. Combat, bots, loot, inventory and match loop
- Add two fictional primary weapons, ammunition/reload/fire, hit feedback, target/bot actors, two teams, healing and match feedback.
- Add loot pickup/interact and backpack inventory with two weapon slots and unlimited item capacity.
- Pass: player can begin at zero bots, add bots, shoot targets, switch weapons, loot, heal and survive a complete session loop.

### 5. HUD, minimap, touch controls and customization
- Build in-match HUD with pause, map/player/FOV indicators, ammo/health/team status, fixed joystick and multi-touch action controls.
- Make mobile controls work independently when simultaneous touches occur; implement fullscreen and draggable HUD layout persistence.
- Pass: essential controls are visible, draggable, and reachable in landscape; minimap updates player/actors and view direction.

### 6. Verification and finish
- Run the app and check JavaScript/build errors and browser rendering; fix obvious defects.
- Verify entry flow, keyboard/mouse controls, menu transitions, bot setup, combat, pause/lobby, settings, layout mode and responsive behavior.
- Capture and inspect a current small JPEG screenshot when a browser harness is available.
- Pass: no blank/loading-only screen, major button paths work, and known limitations are documented.

## Control map
- Desktop: WASD move, Shift sprint (sprint is also the default pace), mouse look, left-click fire, right-click aim, Space jump, C crouch, R reload, F pickup/interact, H heal, Tab backpack, 1/2 weapon select, Esc pause.
- Mobile: fixed left joystick; right-side drag to look; separate aim/fire/jump/crouch/heal/swap/backpack controls designed for simultaneous touch.

## Progress log
- Step 1: complete. Workspace inspected; an original Three.js browser-based offline shooter is the appropriate scope and all major requirements/acceptance checks are recorded above.
- Step 2: complete. Lobby, Offline/Online/Settings/Layout navigation, independent 0–8 bot steppers, responsive screens, and match entry are implemented and covered by Chromium smoke checks.
- Step 3: implementation complete; verification partial. Procedural battlefield, first-person camera, keyboard/mouse and fixed touch movement/look controls are implemented. Chromium rendering was inspected at desktop and mobile sizes; movement feel and real-device touch still need hands-on validation.
- Step 4: implementation complete; core interaction checks passed. Chromium checks verified firing consumes ammo, reload restores it, a hostile bot damages the player, the field dressing action reports `FIELD DRESSING APPLIED +45`, and an in-reach pickup removes the world loot, adds it to inventory, and reports `SECURED`. The pickup test positioned the player at a loot item to isolate the interaction; ordinary exploration to locate loot was not tested. The post-heal health read overlapped incoming bot damage, so it is not a clean measurement of net healing.
- Step 5: implementation complete; browser verification passed. HUD, minimap, simultaneous touch input, pause, and persistent layout editing are implemented. Multi-control touch dispatch and layout flows passed Chromium checks. Fullscreen was successfully entered using a real Chromium CDP mouse gesture (not a synthetic DOM `.click()`).
- Step 6: complete for the available browser harness. `npm run build` succeeds and Chromium smoke tests cover the lobby, match/HUD, pause/backpack/layout, touch fire/aim/movement, ammo use/reload, damage/healing feedback, loot pickup, and fullscreen. Desktop/mobile screenshots were captured and inspected. Physical-device touch ergonomics and gameplay balance remain untested.

## Known limitations and remaining verification
- Online is intentionally a nonfunctional placeholder; there is no server, matchmaking, accounts, or networking.
- This is a procedural offline prototype, not a content-complete commercial shooter. Bot behavior is simple local sparring AI; there is no objective/win-condition or progression loop.
- Environment and actors use generated geometry. Browser rendering was checked, but gameplay balance, collision edge cases, and touch ergonomics have not been play-tested on physical devices.
- Automated gameplay checks confirm firing/ammo/reload, simultaneous touch input, hostile damage, healing feedback, the in-range loot pickup interaction, and gesture-authorized fullscreen. Loot discovery during ordinary exploration was not checked, and incoming fire prevented isolating the exact net health gain from healing.
- Physical-device touch ergonomics, gameplay balance, collision edge cases, and longer-session stability still need hands-on testing. The production bundle builds, with Vite's advisory warning that the minified main chunk exceeds 500 kB.
