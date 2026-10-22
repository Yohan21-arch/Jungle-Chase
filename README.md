# Jungle Chase

A three-lane endless runner built with HTML, CSS, and JavaScript. Run along a cracked yellow-grey jungle road, dodge or jump over holes, and stay ahead of a stylized Narendra Modi character.

The character is AI-generated artwork used in a fictional arcade game. It does not imply endorsement or depict a real event.

## Getting started

1. Download and extract `jungle-chase-updated.zip`.
2. Keep these files in the same folder:

   ```text
   index.html
   style.css
   game.js
   README.md      (optional documentation)
   ```

3. Open `index.html` in a modern web browser.
4. Select **Let’s run**, or press **Space** or **Enter**.

No installation, build process, server, or internet connection is required. The character image is embedded in `game.js`.

## How to play

Your character runs forward automatically. Move between the three lanes to avoid holes, or jump just before a hole reaches your feet. If you reach a hole without enough jump height, the chaser catches up and the run ends.

Try to travel as far as possible. The pace gradually increases, and later sections can have holes in two lanes at once. Select **Run again** to restart after being caught.

## Controls

| Action | Keyboard | Touch |
| --- | --- | --- |
| Move left | Left arrow or A | Left button or swipe left on the game |
| Move right | Right arrow or D | Right button or swipe right on the game |
| Jump | Space, Up arrow, W, or Enter during a run | Jump button, tap the game, or swipe up |
| Pause or resume | P or Escape | Pause/resume button at the top right |
| Start, restart, or resume from the overlay | Space or Enter | Main overlay button |

The game automatically pauses when the browser window loses focus or the tab becomes hidden. Resume when ready.

## Features

- Three lanes with smooth lane changes.
- A straight, cracked yellow-grey road with stone border walls.
- Jungle scenery with trees, hills, and warm lighting.
- Jagged holes with shaded inner walls, broken rims, stones, and surrounding cracks.
- Pseudo-3D perspective, shaded runner limbs, alternating strides, shadows, and subtle camera motion.
- An embedded, stylized Narendra Modi sprite with bobbing motion.
- Distance tracking, gradually increasing difficulty, and restart controls.
- Personal-best storage in the browser when local storage is available.
- Responsive layout and touch controls.

## Project files

| File | Purpose |
| --- | --- |
| `index.html` | Page structure, game canvas, score display, menus, and controls. |
| `style.css` | Layout, colors, typography, responsive sizing, and button styling. |
| `game.js` | Game loop, input, movement, jumping, hazards, collisions, rendering, and embedded character image. |

## How it works

The game draws onto an HTML Canvas using its 2D rendering context. Perspective projection, layered scenery, gradients, and shadows create a 3D-like appearance; this is not a full 3D engine.

Animation uses `requestAnimationFrame`. Simulation updates use elapsed time and small substeps to check collisions reliably. Long frame delays are capped, so the game may slow down on a severely overloaded device rather than skipping a large stretch of road.

Each hole belongs to a lane and moves toward the runner. When it reaches the collision position, the game checks the runner’s lane and jump height.

## Customization

Edit the files in any text editor, save, and reload the browser.

- **Page text and title:** edit `index.html`.
- **Interface colors and sizing:** edit `style.css`, starting with the `:root` variables.
- **Jump duration:** change `jumpDuration` in `game.js`.
- **Running and obstacle speeds:** adjust the calculations inside `update()`.
- **Hole frequency:** adjust the `spawn` interval in `update()`.
- **Hole appearance:** edit `drawHole()`.
- **Runner appearance:** edit `person()`.
- **Road perspective:** edit `perspective()` and `project()` together, then check visual alignment with collisions.
- **Chaser artwork:** replace the data URL assigned to `modiImage.src`. A transparent PNG works best. Using an external image file instead requires distributing that file alongside the game.

The embedded image makes `game.js` larger than a typical script. Search for function names to navigate past the image data.

## Troubleshooting

**The page is unstyled or the game does not start**

Ensure `index.html`, `style.css`, and `game.js` are extracted into the same folder with their original names. Do not open the HTML directly inside a ZIP viewer.

**The game pauses unexpectedly**

Switching tabs or moving focus away from the browser pauses the run automatically. Use the resume button, Space, Enter, P, or Escape to continue.

**The personal best does not persist**

Browser privacy settings or restrictions on local files may block local storage. Gameplay still works, but the score may not survive closing the page. The existing storage key is `monkey-run-best`, retained from the original version.

**Animation is slow**

Close other busy tabs or try a smaller browser window. Rendering performance depends on the device and browser.

## Verification and limitations

JavaScript syntax and automated logic checks passed for lane bounds, pause/resume, collisions, getting caught, restarting, jumping, dodging, and spawning. A mocked canvas render smoke check also passed.

Visual browser verification was not completed because the preview connection timed out. Appearance and touch behavior have not been confirmed across browsers or physical devices.

The chaser uses a single generated sprite with movement effects, rather than a fully rigged 3D character or a multi-frame running sprite sheet.
