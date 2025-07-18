# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**ninja_rogue** - A game development project for creating action/survival games using Python (Pygame) or TypeScript. Currently exploring implementations similar to Vampire Survivors. Licensed under Apache 2.0.

## Repository Structure

```
ninja_rogue/
├── game_name/            # Each game in its own directory
│   ├── src/             # Game source code
│   │   ├── main.py      # Entry point
│   │   ├── player.py    # Player mechanics
│   │   ├── enemy.py     # Enemy systems
│   │   └── ...          # Other game modules
│   ├── assets/          # Game assets
│   │   ├── images/      # Sprites and graphics
│   │   └── sounds/      # Audio files
│   └── README.md        # Game-specific documentation
├── .devcontainer/       # VS Code dev container setup
└── .github/workflows/   # CI/CD pipelines
```

## Development Setup

The project uses VS Code Dev Containers with Docker for a consistent development environment.

### Quick Start
```bash
# Build and start development container
make up

# Start Claude Code AI assistant (new session)
make claude

# Continue previous Claude session
make continue

# Enter container shell for manual commands
make shell
```

### Container Management
```bash
make pause     # Pause running container
make unpause   # Resume paused container
make stop      # Stop container
make down      # Remove container completely
make rebuild   # Full rebuild (down + up)
make status    # Check container status
```

## Common Commands

### Running Games
```bash
# Python/Pygame games
python game_name/src/main.py

# TypeScript games (when implemented)
npm start --prefix game_name
```

### Development Workflow
```bash
# Install Python dependencies
pip install pygame

# Run tests (when implemented)
pytest

# Type checking
mypy game_name/src/

# Linting
ruff check game_name/src/

# Security scanning
bandit -r game_name/src/
```

### Python Environment
- **Supported Versions**: Python 3.10-3.13
- **Game Framework**: Pygame (for Python implementations)
- **Package Manager**: pip
- **Virtual Environment**: Handled by devcontainer

## Architecture Notes

### Game Architecture (Python/Pygame)
Common patterns for game implementations:

1. **Main Game Loop** (`main.py`)
   - Handle events, update game state, render
   - Manage game scenes/states

2. **Entity System**
   - **Player**: Character control, abilities, stats
   - **Enemies**: AI behavior, spawning patterns
   - **Projectiles**: Weapon systems, collision detection
   - **Power-ups**: Temporary/permanent upgrades

3. **Game Systems**
   - **Collision Detection**: Sprite groups, rect collisions
   - **Wave Management**: Enemy spawning, difficulty scaling
   - **Score/Progress**: High scores, achievements
   - **Audio**: Background music, sound effects

### Key Development Principles
- **KISS**: Keep It Simple, Stupid
- **DRY**: Don't Repeat Yourself  
- **YAGNI**: You Aren't Gonna Need It
- **SOLID**: Single responsibility, Open/closed, etc.
- **TDD**: Test-Driven Development approach
- **Boy-Scout Rule**: Leave code cleaner than found

## Testing

### Test Structure
```bash
# Run all tests for a game
pytest game_name/tests/

# Run specific test file
pytest game_name/tests/test_player.py

# Run with coverage
pytest --cov=game_name/src game_name/tests/

# Run specific test
pytest game_name/tests/test_player.py::test_movement
```

### CI/CD Pipeline
- **Multi-version Testing**: Python 3.10-3.13
- **Automated Checks**: Linting, type checking, security scanning
- **PR Reviews**: Automated Claude AI code reviews on pull requests
- **Note**: CI expects basic project structure to exist

## Development Guidelines

1. **Always create feature branches** - Never commit directly to main
2. **Follow conventional commits** - Use prefixes like `feat:`, `fix:`, `test:`
3. **Write tests first** - TDD approach for all new features
4. **Keep games modular** - Each game in its own directory
5. **Use type hints** - All functions should have proper type annotations
6. **Document game controls** - Include controls in game README

## External Dependencies

### For Python Games
- **Pygame**: Game development framework
- **pytest**: Testing framework
- **mypy**: Type checking
- **ruff**: Linting
- **bandit**: Security scanning

### Infrastructure
- **Docker**: Development environment containerization
- **GitHub Actions**: CI/CD automation

## Current Games

- **vampire_survivors** (PR #2): A Vampire Survivors-style game implementation in Python/Pygame

## Future Considerations

- TypeScript/JavaScript game implementations
- Web-based game versions
- Mobile game adaptations