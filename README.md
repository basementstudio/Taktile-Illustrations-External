# Taktile illustration motion

Hover-animation prototypes for Taktile's isometric illustrations (external version).

Published preview: https://claude.ai/artifact/Uuheq1CujWzzWozDJxCH86

Four animations:

1. **Connect**: two slabs collide and fuse into one cube; the seam zips shut behind a spark
2. **Decide** (Figma 8050:7894): four equal layers that make one cube; the hovered layer widens to both sides and the layers around it narrow, so the cube keeps its size
3. **Optimize** (the brand icon, Figma 8050:8025; ported from the 02 of tomasv912/Taktile-Claude-Illustrations): two versions, switched with the card's arrows, both played once on the first hover of the shape and then staying on the brand icon, where the hovered layer slides right (Shift) and its neighbours follow. v1 (reveal): the layers come out of each other's front face one after another and slide into place, their back edges going grey → white. v2 (split): Connect backwards, one block shudders as its cuts open, then the pieces fly apart into place
4. **Scale** (loop): the window scales up and extrudes at once into the big cube, while the old cube flattens toward the back and fades; then a new window opens. The cube lies on its side by default (Figma 7907:5126); the **Straight cube** toggle (Customize parameters) stands it upright

All cards are drawn procedurally from the Figma frames' geometry. Inner edges are solid lines (#353232 dark, #9A9797 light); the white outline is 1.5px on screen. Only 03 has more than one version (arrows on the card); it moves on 04's sharp-peak grow curve.

Under each card's title, a step badge (Figma 8451:3801 / 3827 / 3849 / 3870) shows the four pillars in order with the card's own one lit in its colour.

Layers that have fully faded leave the render tree (`display: none`), so their blur panes can't leave a faint ghost line behind.

- The side panel only holds what every animation shares: Motion (Speed, Bounce, Fades, Start/stop) and Hover (Color per animation, Follow pointer). The hover spring uses the Butter curve, the background blur is fixed at 5px and the hover tint is the theme grey.
- **Color per animation** gives each card its own hover colour: 01 Connect #2386CF, 02 Decide #463ECC, 03 Optimize #C98C2D, 04 Scale #0E9755.
- Each card's own settings live in a collapsed **Customize parameters** dropdown inside that card.
- Loops always return to rest when the pointer leaves.

## Font

The page is set in Söhne (Klim Type Foundry), a licensed font that isn't bundled here. It is used when installed locally, or when the licensed webfonts are placed in `fonts/` next to `index.html`:
`soehne-buch.woff2`, `soehne-kraftig.woff2`, `soehne-mono-buch.woff2`, `soehne-mono-kraftig.woff2`. Without them the system sans is used.

## Files

- `index.html` — the built page (published as the artifact). Don't edit by hand.
- `src/template.html` — page source: styles, markup and all animation code.
- `src/build.mjs` — writes `index.html` from the template.
- `serve.mjs` — local preview server (wraps the page the way the artifact host does).

## Build and preview

```bash
node src/build.mjs
node serve.mjs
```

Then open http://localhost:5173 (set `PORT` to use another port).
