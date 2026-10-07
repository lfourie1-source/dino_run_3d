# Generative AI Tools and Models Used

## Coding / Design Assistance
**OpenAI ChatGPT — GPT-5.6 Sol**

Used for:
- HTML/CSS/JavaScript game prototyping.
- Procedural obstacle and difficulty-system design.
- Collision and scoring logic.
- Debugging reversed controls and safe-lane exploits.
- Audio integration.
- Project packaging and documentation.

The human creator repeatedly play-tested the output, identified failures, selected the art direction, chose the gameplay rules, and requested revisions.

## Audio Generation
**ElevenLabs**

ElevenLabs was used to generate the custom audio used in the game:
- background music
- death sound effect
- jump sound effect
- victory / biome-change sound effect

The generated audio files are stored in `assets/audio/`.

## Visual Generation
No external generative-image assets are used in the submitted game. The dinosaur, environment, obstacles, coins, and biome visuals are drawn by code in `src/game.js`.
