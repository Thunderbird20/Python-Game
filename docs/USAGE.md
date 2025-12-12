# Usage

This document explains how to play and configure the game.

Running the game

```bash
python -m src.main
```

Command-line options (example)
- `--fullscreen` — start the game in fullscreen mode
- `--debug` — enable debug logging and on-screen diagnostics

Settings

The project may include a `config/` directory or an INI/JSON/TOML file for
runtime configuration. Typical settings:
- `resolution` — screen width and height
- `volume` — master audio level
- `difficulty` — game difficulty

Saving & Profiles

Save files are typically stored under `~/.local/share/python-game/` on Linux or
`%APPDATA%\Python-Game` on Windows. The save format is JSON by default.

Troubleshooting

- If assets are missing, ensure the `assets/` folder exists and contains
  the required image/audio files.
- If a dependency import fails, run `pip install -r requirements.txt`.
