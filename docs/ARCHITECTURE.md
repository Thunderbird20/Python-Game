# Architecture Overview

This document describes the project's high-level architecture, component
responsibilities, data flow, and extension points.

Repository layout (recommended)
- `src/` — application source code
  - `src/main.py` or `src/main/__init__.py` — entry point that starts the
    game and handles argument parsing.
  - `src/game/` — core gameplay code: `game_loop.py`, `entities.py`,
    `level.py`, `collision.py`.
  - `src/render/` — rendering layer: canvas, sprite management, UI/HUD.
  - `src/input/` — input handling and mapping (keyboard/gamepad).
  - `src/audio/` — audio playback and volume controls.
  - `src/config/` — runtime configuration and defaults.
- `assets/` — images, audio, fonts, level data.
- `docs/` — documentation (this folder).
- `tests/` — unit and integration tests.

Primary components and responsibilities
- Entry point: initializes logging, configuration, and the main game object.
- Game loop: fixed-step or variable-step loop that updates game state,
  processes input, updates physics, then renders the frame.
- Entities: objects in the world (player, enemies, items) with update and
  render methods.
- Renderer: abstracts drawing so the core logic is display-agnostic; supports
  console and Pygame implementations.
- Input manager: normalizes input events into high-level actions (e.g.,
  "move_left", "jump").
- Asset manager: loads and caches images/sounds; returns fallback assets when
  missing.
- Persistence: save/load system for player profiles and progress (JSON by
  default).

Data flow (startup -> game)
1. Read configuration and CLI flags.
2. Initialize subsystems: assets, audio, input, renderer.
3. Load first level and player profile.
4. Enter main loop: handle input -> update world -> render frame -> flush audio.

Extensibility points
- New renderer backends: implement the renderer interface and swap via
  configuration.
- New entity types: inherit a base `Entity` class and register in the
  level loader.
- Level format: JSON or custom text files; support an editor export pipeline.

Performance and portability
- Keep game logic separate from rendering to facilitate headless testing.
- Use simple data formats (JSON) for saves and level data for portability.

Testing strategy
- Unit test core gameplay rules in `tests/` without the renderer.
- Use small integration tests that run a few game-loop steps in headless
  mode to validate state transitions.

Diagram (textual)

  [CLI/Launcher] -> [Config] -> [Main] -> {AssetMgr, InputMgr, AudioMgr, Renderer}
                                    |
                                    v
                                [Game Loop]
                                    |
                                    v
                             [Levels] <-> [Entities]

Security & safe defaults
- Validate and sandbox loaded level files and external assets.
- Limit paths for save/load to project or user data directories.

Deployment notes
- For desktop: package with `pyinstaller` or provide a small launcher.
- For distribution: include `requirements.txt` and a `README` with
  system package notes (SDL on Linux when using Pygame).
