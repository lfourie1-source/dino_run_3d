# Master AI Prompt Log — Blocky Dino Dimension Run

This log summarizes the major prompts, corrections, and design decisions in chronological order. Short prompt quotations preserve the actual intent of the development conversation while removing repeated back-and-forth that did not change the project.

## 1. Initial Concept
**Prompt:** “Let’s make a browser game in HTML like the Google no-internet game, but make it 3D and third person looking from behind the dino.”

**Result:** A third-person endless-runner prototype was created with a dinosaur viewed from behind.

**Human direction:** The game needed actual forward movement rather than a flat side-view clone.

## 2. Real Movement and Blocky Arcade Style
**Prompt:** “Make the graphics better… make it look blocky and arcade like. Make the dino move; don’t use visual tricks to make it look like it’s moving.”

**Result:** The visual direction became blocky/arcade-inspired and the dinosaur/world used forward-motion gameplay.

## 3. Dino Scale and Jump Controls
**Prompt:** “Make the dino smaller… also it doesn’t jump when I press space.”

**Result:** Dinosaur size was reduced and Space/Up Arrow jump handling was fixed.

## 4. Steering Bug
**Prompt:** “The A/D keys are flip-flopped.”

**Problem:** Horizontal steering was reversed from the player’s perspective.

**Resolution:** Controls were corrected so A/Left Arrow moves left and D/Right Arrow moves right.

## 5. Black-and-White Art Direction
**Prompt:** “Make the game black and white.”

**Result:** Dimension 1 was changed to a high-contrast monochrome arcade look.

## 6. Harder Gameplay
**Prompt:** “Make the game significantly harder.”

**Result:** Obstacle density, speed growth, collision pressure, and multi-obstacle patterns were increased.

## 7. Safe-Lane Exploit — First Discovery
**Prompt:** “I can run through the right side of the obstacles forever and beat the game.”

**Problem:** The procedural generator left an exploitable path that did not require player input.

**Initial response:** Side boundaries and more varied lane blockers were added.

## 8. High Score and Dimension Mechanic
**Prompt:** “Add a highscore counter and… if you get to 500 score you travel to a new dimension.”

**Result:** Persistent high score was added with `localStorage`, and biome shifts were triggered every 500 points.

## 9. Dimension Art Direction
**Prompt:** “Make the dimension shift give it color… going back to normal from black and white; then the 3rd dimension shift was fine.”

**Result:** Dimension 2 became a full-color desert, while Dimension 3 retained the dark/void style.

## 10. Safe-Lane Exploit — Second Discovery
**Prompt:** “I am not touching my keyboard yet my score is going up.”

**Problem:** Even after randomization, a deterministic straight path still existed.

**Final fix:** Mandatory full-width jump hurdles were introduced. Because these cover the complete drivable width, a player who never jumps cannot survive indefinitely.

## 11. UI Cleanup
**Prompt:** “Remove the messages at the bottom please.”

**Result:** The persistent bottom instruction banner was removed from the desktop game UI.

## 12. Background Music and Death Sound
**Prompt:** Add the supplied music as looping background audio and play `dying.mp3` when the player dies.

**Result:** Music loops during play and a death sound triggers on collision.

**Browser issue encountered:** Browser autoplay restrictions required audio to begin only after a user clicks PLAY or otherwise interacts with the page.

## 13. Broken Single-File HTML / Source Display Issue
**Problem:** Several oversized single-file exports with embedded base64 audio displayed poorly or behaved unreliably when opened/downloaded.

**Recovery:** The project was rebuilt with a normal `index.html`, separate source files, and organized audio files. This keeps the playable entry point small and matches standard web-project structure.

## 14. Music-on-Death Behavior
**Prompt:** “The music should stop when I die and make the dying sound effect louder.”

**Result:** Background music stops immediately at game over, resets to the beginning, and the death effect plays at full volume.

## 15. Steering Regression
**Prompt:** “The A/D keys are flip-flopped again.”

**Problem:** A later revision accidentally reintroduced reversed steering.

**Resolution:** The movement mapping was corrected without changing the audio behavior.

## 16. Roadside Scenery Iteration
**Prompt sequence:** Add trees, then move them closer to the dino, then replace them with “small cactii right in front of it.”

**Result:** Trees were removed and replaced by small blocky cacti better matching the desert/arcade aesthetic.

## 17. Cacti Become Gameplay Obstacles
**Prompt:** “Make those cactii obstacles… they should appear there sometimes because otherwise we can just stay in that area and not move and get hella points.”

**Result:** Small inner-line cacti became real collision hazards and were randomized so they create occasional lane pressure instead of constant clutter.

## 18. Jump Sound
**Prompt:** “Add this sound effect every time I jump, i.e. every time I press the space bar.”

**Result:** The supplied jump effect was connected to successful jumps. Excess silence in the original clip was trimmed so repeated jumping feels responsive.

## 19. Progressive Difficulty and Coins
**Prompt:** “Make it easier starting off then make it harder as the score progresses; also add some coins you can get that gives you plus 10 score.”

**Result:** The first portion of a run now has slower speed, larger gaps, and simpler patterns. Difficulty ramps through several bands as score rises. Gold coins were added as optional pickups worth +10 points.

## 20. Biome Victory Sound
**Prompt:** “Everytime the biome changes add this victory sound.”

**Result:** The supplied victory chime plays once whenever the player crosses a 500-point dimension threshold.

---

# Error-Recovery Summary

### Safe-lane hallucination / design failure
The first procedural systems looked varied but did not guarantee interaction. Manual testing proved that “random” did not automatically mean “unexploitable.” The fix was a deterministic rule: periodically create a full-width hurdle that can only be cleared by jumping.

### Reversed controls
Steering direction regressed during revisions. The fix was to test controls from the camera/player perspective after every movement-related edit and preserve A=left, D=right as a fixed requirement.

### HTML/audio packaging failure
Embedding several MP3 files directly as base64 made the HTML extremely large and unreliable as a downloadable classroom submission. The recovery was to separate assets into `assets/audio/`, keep `index.html` lightweight, and move game logic and styles into dedicated source files.

### Browser autoplay restriction
Audio could not reliably autoplay on page load. The solution was to start audio only after the PLAY button provides a browser-approved user gesture.

---

# Analytical Reflection
See `REFLECTION.md` for the 200–300 word reflection submitted with this log.
