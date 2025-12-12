# Development Guide

This guide helps new developers set up the project for development and testing.

Local dev setup

1. Follow [docs/INSTALLATION.md](docs/INSTALLATION.md) to prepare the
   environment.
2. Install developer dependencies (if separate) or the same `requirements.txt`.

Testing

- Unit tests (example):

  ```bash
  pytest
  ```

Debugging

- Use `--debug` mode (if present) to enable logging and visual helpers.
- Attach a debugger to `src/main.py` or set breakpoints in your editor.

Code formatting

- Run `black` for automatic formatting and `flake8`/`pylint` for linting.
