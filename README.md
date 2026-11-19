# Blasteroids: an arcade game on an FPGA

Group project for 02113 Digital Systems Design Project at the Technical University of Denmark, 2025.

The game is inspired by *Asteroids*. The player flies a ship up and down the left side of the screen and shoots rockets at asteroids coming from the right. Three hits and the game is over. It runs on an FPGA board with VGA output, and is controlled with the board's buttons.

**Game logic (`GameLogic.scala`, written in Chisel)**

- A 9-state FSM runs once per frame: move player → spawn asteroids → spawn rockets → move sprites → detect collisions → (circle check) → animate → done.
- Random asteroid size, position, speed and spawn interval come from an 8-bit LFSR. The LFSR is seeded by how long the player waits before pressing start.
- Collision detection has two stages: a cheap bounding-box test, then an exact circle test only when needed. The checks are spread across frames to keep each frame's logic small.
- Extras: a scrolling background, start and end screens, explosion animations scaled to the asteroid's size, spinning asteroids (sprite flipping) and flashing hearts when the player gets hit.

**My part:** main developer. I wrote most of the game logic.

**Report:** [Report.pdf](Report.pdf)

*The project builds on the course's graphics/sound engine framework (© DTU). Only the game logic is ours.*
