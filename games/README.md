# Games Directory

This directory contains all game implementations. Each game is self-contained with its own technology stack.

## Directory Structure

Each game should follow this pattern:
```
game_name/
├── src/                 # Source code
├── assets/              # Game-specific assets
├── tests/               # Unit and integration tests
├── README.md            # Setup and documentation
└── requirements.txt     # (Python) or package.json (JavaScript)
```

## Current Games

- `vampire_survivors/` - Wave-based survival game (Python/Pygame)

## Adding a New Game

1. Create a new directory with your game name
2. Include a README with:
   - Technology stack used
   - Setup instructions
   - How to run the game
   - Game controls
   - Architecture decisions
3. Keep all game-specific code and assets within the directory
4. Use the `shared/` directory for truly reusable components