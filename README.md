# SEY GAMERZ ESCAPE ROOM — 50-ROOM CAMPAIGN

A host-controlled collective survival-horror escape-room web game. The complete campaign contains 10 missions with five rooms each.

## Campaign content
- 10 missions / 50 individually named rooms.
- 250 clickable room objects with hidden-note interactions.
- 250 room-specific clue notes; four numeric deduction clues and one lock-order/mechanism note per room.
- 50 distinct four-digit room solutions.
- Mission-specific object vocabularies and 50 distinct five-object arrangements.
- Individual room objectives and escalating room timers.
- Ten visual mission treatments and room-specific hotspot layouts.

## Gameplay rules
- One collective team; one host-operated interface.
- No player accounts, teams, leaderboard, XP, or individual rewards.
- Shared wallet starts at 5,000 Escape Coins (EC) at the beginning of each new mission.
- Submission fees: 100 / 150 / 200 / 250 / 300 EC (5th attempt onward).
- Every valid four-digit submission is charged before answer checking. Wrong answers are not refunded.
- The host starts, pauses, and resumes each room timer. Timer expiry cancels the entire mission.
- Correct answers unlock the next room. The fifth correct answer completes the mission.
- Hint shop, host wallet adjustment, and mission cancellation are available from the host panel.
- Current progress is saved in localStorage on the same browser/device.

## Run locally
Requires Node.js 20 or later. No external npm packages are required.

```bash
npm run dev
```

Open `http://localhost:4173`.

Build the static production site:

```bash
npm run build
```

The deployable site is written to `dist/`.

## Deploy to Render
1. Push this folder to a GitHub repository.
2. In Render, choose **New → Static Site** and connect the repository.
3. Build command: `npm run build`
4. Publish directory: `dist`
5. Deploy. The included `render.yaml` can also be used as a Blueprint.

## Deploy to GitHub Pages
1. Push the project to the `main` branch of a GitHub repository.
2. In repository **Settings → Pages**, select **GitHub Actions** as the source.
3. The included `.github/workflows/deploy.yml` builds and deploys the static site on every push to `main`.

## Production limitations to understand before public launch
- The project is a static, browser-based host game. Save data lives in that browser's localStorage and does not sync across devices or between multiple hosts.
- The 50 rooms have distinct story objectives, room names, object combinations, clues, codes, timers, and mission-specific visual treatments. The current build uses one supplied mansion scene plate with different visual grading/layouts; 50 individually illustrated cinematic room backgrounds have not been commissioned yet.
- Puzzle answers are stored in client-side JavaScript. This is suitable for a trusted host-operated community game, but not secure against someone inspecting browser files. A server-backed API, host authentication, and shared database are needed for tamper-resistant multi-device play.
- Sound effects are generated in the browser using Web Audio after user interaction.


## Room artwork (50 unique assets)

The `assets/rooms/` folder now contains 50 separate original 1600×900 SVG scene files: five different scenes for each of the ten missions. The game selects the matching file automatically for the current mission and room. These are vector scene illustrations, not 50 reused copies of the mansion reference image. They are lightweight, scale cleanly on phones and laptops, and are included in the production build.

To verify the artwork inventory, run `npm run validate`. The validator checks that all 50 individual room image files exist and are distinct.
