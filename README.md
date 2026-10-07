# Blocky Dino Dimension Run

## Project Summary
Blocky Dino Dimension Run is a third-person-style browser endless runner inspired by the simple survive-and-jump loop of the Chrome offline dinosaur game. The player controls a blocky dinosaur, avoids obstacles, collects coins, and enters a new biome every 500 points.

## How to Run
1. Keep the project folder structure unchanged.
2. Open `index.html` in Google Chrome, Microsoft Edge, Firefox, or another modern browser.
3. Click **PLAY** to begin. Browser audio starts after this user interaction.

No build step, package manager, or internet connection is required.

## Controls
- **A / Left Arrow:** move left
- **D / Right Arrow:** move right
- **Space / Up Arrow:** jump
- **R:** restart after game over
- Mobile browsers show on-screen left, jump, and right buttons.

## Core Game Loop
- **Reward:** collect a coin for **+10 score**.
- **Damage / Failure:** colliding with a cactus, rock, or full-width hurdle ends the run.
- **End:** the game-over screen displays the current score and high score.
- **Progression:** the game starts slower and easier, then speed and obstacle density increase as score rises.
- **Biome shifts:** every 500 points the game changes dimension/biome and plays a victory sound.

## Biomes
- **Dimension 1:** black-and-white arcade world.
- **Dimension 2:** full-color desert world.
- **Dimension 3+:** dark/void world.

## Audio
Audio assets are organized under `assets/audio/`:
- `background.mp3` — looping gameplay music.
- `dying.mp3` — game-over sound; background music stops first.
- `jump.mp3` — jump sound effect.
- `victory.mp3` — biome/dimension transition sound.

## Source Architecture
- `index.html` — entry point and game UI.
- `assets/css/styles.css` — presentation and responsive/mobile controls.
- `src/game.js` — game state, movement, procedural obstacle generation, collision detection, score/high-score system, dimensions, coins, rendering, and audio events.
- `assets/audio/` — audio files.

## AI Documentation
- `PROMPT_LOG.md` — chronological prompt and debugging record.
- `REFLECTION.md` — 200–300 word analytical reflection.
- `REFERENCES.md` — concept, gameplay, visual, and acoustic references.
- `AI_TOOLS.md` — generative AI inventory.
- `ATTRIBUTION.md` and `ASSET_ATTRIBUTION.csv` — asset source/terms notes.

## Submission Note
The exact AI audio-generation service/model used to create the uploaded audio files was not recorded in the development conversation. The attribution files flag this clearly so the creator can add the exact service name/terms if required by the instructor.
