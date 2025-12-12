# Installation

This document explains how to set up the project locally.

Requirements
- Python 3.10+ (3.8+ may work but newer is recommended)
- `pip` for package installation

Recommended: create and use a virtual environment.

Steps

1. Clone the repository:

   ```bash
   git clone <repo-url>
   cd Python-Game
   ```

2. (Optional) Create a virtual environment:

   ```bash
   python -m venv .venv
   source .venv/bin/activate
   ```

3. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```

4. Run the game (example entrypoint):

   ```bash
   python -m src.main
   ```

If the project uses Pygame or other libraries, additional system packages
may be required on Linux (e.g., SDL development packages). Refer to the
project's `requirements.txt` for the exact dependencies.
