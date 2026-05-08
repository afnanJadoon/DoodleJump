# Doodle Jump — C++ / SFML Clone

A clone of the classic mobile game **Doodle Jump**, built with **C++** and the **SFML** graphics library as an Object-Oriented Programming (OOP) project.

---

## Gameplay

Control a character that automatically jumps on platforms to climb as high as possible. The higher you go, the better your score!

### Controls

| Key | Action |
|-----|--------|
| `←` / `A` | Move Left |
| `→` / `D` | Move Right |
| `R` | Restart after Game Over |

---

## Features

### Core Gameplay
- Automatic jumping when landing on platforms
- Left/right movement with screen wrapping (walk off one edge, appear on the other)
- Realistic gravity physics

### Visuals
- Custom sprite support for the player character (Goku skin included)
- Smooth camera that follows the player upward — never scrolls down
- Green platforms with colored fallback shapes if textures are missing

### Audio
- Jump sound effect (plays when the player bounces)

### Game Systems
- **Score Tracking** — score increases as you climb higher
- **High Score** — your best run is remembered during the session
- **Game Over Screen** — shows your final score when you fall
- **Restart** — press `R` to play again instantly

### Technical
- 60 FPS gameplay with delta-time based physics
- Random platform generation as you ascend
- Collision detection between player and platforms

---

## Project Structure

```
DoodleJump/
├── source/
│   ├── main.cpp          # Entry point
│   ├── GameObject.h/.cpp # Base class for all game objects
│   ├── Player.h/.cpp     # Player movement, jumping, gravity
│   ├── Platform.h/.cpp   # Platform rendering & collision
│   ├── Camera.h/.cpp     # Upward-only scrolling camera
│   ├── Game.h/.cpp       # Main game loop & state manager
│   ├── player.png        # Player sprite (optional)
│   ├── jump.wav          # Jump sound effect (optional)
│   └── arial.ttf         # Font file (optional)
└── README.md
```

---

## Class Overview

### `GameObject`
Base class inherited by all game objects. Handles position, velocity, texture loading, and rendering. Falls back to a colored shape if no texture is found.

### `Player`
- Reads keyboard input for left/right movement
- Applies gravity each frame
- Triggers a jump when landing on a platform
- Flips the sprite horizontally based on movement direction

### `Platform`
- Rendered as a green rectangle (or custom texture)
- Detects upward collision with the player to trigger a jump

### `Camera`
- Tracks the player's vertical position
- Moves the view upward as the player climbs
- Never scrolls downward (just like the original game)

### `Game`
- Initializes the window, loads assets, and generates starting platforms
- Runs the main game loop: input → update → collision → camera → render
- Manages game states: **Playing** and **Game Over**

---

## How to Build

### Requirements
- C++17 or later
- [SFML 2.x](https://www.sfml-dev.org/download.php)
- A C++ compiler (MSVC, GCC, or Clang)

### Build with Visual Studio
1. Open the project in Visual Studio
2. Link the SFML libraries in Project Properties → Linker → Input
3. Make sure SFML `.dll` files are in the same folder as the executable (for debug builds, use the `-d` variants)
4. Build and run (`Ctrl+F5`)

### Build with g++ (Linux/macOS)
```bash
g++ source/*.cpp -o DoodleJump -lsfml-graphics -lsfml-window -lsfml-audio -lsfml-system
./DoodleJump
```

---

## ptional Assets

Place these files inside the `source/` folder:

| File | Purpose |
|------|---------|
| `player.png` | Custom player sprite |
| `jump.wav` | Jump sound effect |
| `arial.ttf` | Custom font for score display |

The game runs without these files — it will use default shapes and no audio.

---

## Concepts Demonstrated

- Object-Oriented Programming (Inheritance, Encapsulation, Polymorphism)
- Game loop architecture
- Physics simulation (gravity, velocity)
- Collision detection
- Camera/viewport management
- Asset management (textures, fonts, audio)
- Random procedural generation

---

## Author

**Muhammad Afnan Jadoon**  
OOP Course Project — [Air University / 2nd semester]

