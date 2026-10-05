# Taktile illustration motion

Hover-animation prototypes for Taktile's isometric illustrations (external version).

Published preview: https://claude.ai/artifact/Uuheq1CujWzzWozDJxCH86

Four animations:

1. **Decide** (Figma 8050:7894): four equal layers that make one cube; the hovered layer widens to both sides and the layers around it narrow, so the cube keeps its size
2. **Optimize** (Figma 8050:7808, ported from tomasv912/Taktile-Claude-Illustrations): two versions, switched with the card's arrows. v1: the base grows into the cube and takes the other layers in left to right, each one eaten and fading as its edge passes through it. v2: the layers leave to the right one by one while the base deepens into the cube. **Use brand icon** swaps in the brand icon's layers (Figma 8050:8025) in both
3. **Connect**: two slabs collide and fuse into one cube; the seam zips shut behind a spark
4. **Scale** (loop): rests on the cube with a window open; the window extrudes into a small cube that grows into the new cube, and a new window opens

All cards are drawn procedurally from the Figma frames' geometry. Inner edges are solid lines (#353232 dark, #9A9797 light).

03 and 04 also have an **alternative version**: the arrows on each side of the card switch to it, and its title then ends in "(Alternative version)".

- 01: a conveyor; on hover the last slab slides out right as a new one fades in from the left, and the slab in the third slot is always the thick one
- 02: the same conveyor with the first slot always thick
- 03: the collision and seal, faster; then the block thins back into the thin slab as a new thick one fades in from the left, and it loops
- 04: the window scales up and extrudes at once into the big cube, while the old cube flattens toward the back and fades; then a new window opens

A second alternative (**v3**, "Alternative version 2") keeps the shapes static and plays a move only for the shape under the pointer:

- 01 / 02: the hovered slab takes the thick depth and the thick one thins (only one thick slab at a time); leaving puts it back
- 03: hovering the thick slab plays the collision; hovering the thin one plays it mirrored (the thin one widens left while the thick one thins); leaving plays back
- 04: the cube lies on its side (Figma 7907:5126); hovering its window extrudes it back into a thin block (a quarter of its size deep) while the cube's face recedes to make room; moving off springs back

All alternative versions move on the same sharp-peak speed curve. In 01 and 02 the leaving and arriving slabs travel far past the end slots and narrow out there.

- The side panel only holds what every animation shares: Motion, BG Blur, colour options, Follow pointer, Preview.
- **Color per animation** gives each card its own hover colour: 01 #463ECC, 02 #C98C2D, 03 #2386CF, 04 #0E9755.
- Each card's own settings live in a collapsed **Customize parameters** dropdown inside that card.
- Loops always return to rest when the pointer leaves.
- 04 and its first alternative show the cube on its side by default (Figma 7907:5126); the **Straight cube** toggle (Customize parameters) stands it upright. The animations stay the same.

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
