# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**ninja_rogue** - An experimental game development repository exploring multiple technologies and frameworks. The project serves as a testing ground for implementing games using Python/Pygame, Phaser.js, Babylon.js, HTML5 Canvas, and potentially other frameworks. Licensed under Apache 2.0.

## Repository Structure

```
ninja_rogue/
├── games/                # All game implementations
│   ├── [game_name]/     # Each game in its own directory
│   │   ├── src/         # Source code (structure varies by technology)
│   │   ├── assets/      # Game-specific assets
│   │   ├── README.md    # Setup and run instructions
│   │   └── package.json # (for JavaScript projects)
│   │       requirements.txt # (for Python projects)
├── shared/              # Shared assets and utilities
│   ├── sprites/         # Reusable sprites
│   ├── sounds/          # Reusable audio
│   └── utils/           # Common utilities
├── docs/                # Documentation and design notes
├── tools/               # Development tools and scripts
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

#### Python/Pygame Games
```bash
cd games/[game_name]
pip install -r requirements.txt
python src/main.py
```

#### JavaScript Games (Phaser/Babylon.js)
```bash
cd games/[game_name]
npm install
npm start     # Development server
npm run build # Production build
```

#### HTML5 Canvas Games
```bash
cd games/[game_name]
# For simple games, just open index.html
# For games with modules:
python -m http.server 8000
# Then open http://localhost:8000
```

### Development Workflow

#### Python Projects
```bash
# Create virtual environment (optional, devcontainer handles this)
python -m venv venv
source venv/bin/activate  # Linux/Mac
# or
venv\Scripts\activate     # Windows

# Install dependencies
pip install -r requirements.txt

# Run tests
pytest

# Type checking
mypy src/

# Linting
ruff check src/
```

#### JavaScript/TypeScript Projects
```bash
# Install dependencies
npm install

# Development server with hot reload
npm start

# Run tests
npm test

# Linting
npm run lint

# Type checking (TypeScript)
npm run typecheck
```

### Supported Technologies
- **Python**: 3.10-3.13 with Pygame
- **Node.js**: 18+ for web games
- **TypeScript**: For type-safe JavaScript development
- **Package Managers**: pip (Python), npm/yarn (JavaScript)

## Architecture Notes

### Technology-Specific Patterns

#### Python/Pygame
1. **Main Game Loop** (`main.py`)
   - Handle events, update game state, render
   - Manage game scenes/states

2. **Entity System**
   - Sprite-based with collision groups
   - Component-based design for flexibility

#### Phaser.js
1. **Scene Management**
   - Preload, Create, Update lifecycle
   - Scene transitions and state management

2. **Asset Pipeline**
   - Texture atlases for performance
   - Audio sprites for sound effects

#### Babylon.js
1. **3D Scene Graph**
   - Meshes, materials, and lighting
   - Camera systems for different perspectives

2. **Physics Integration**
   - Built-in physics engines (Cannon.js, Oimo.js)
   - Collision detection and response

#### HTML5 Canvas
1. **Render Loop**
   - requestAnimationFrame for smooth rendering
   - Manual sprite management

2. **Optimization**
   - Object pooling for performance
   - Efficient collision detection algorithms

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
5. **Use appropriate typing**:
   - Python: Type hints for all functions
   - TypeScript: Strict mode enabled
   - JavaScript: JSDoc comments for type information
6. **Document each game**:
   - README with setup instructions
   - Game controls and mechanics
   - Technology choices and rationale
7. **Share learnings** - Document what worked and what didn't

## External Dependencies

### Python Stack
- **Pygame**: 2D game development
- **pytest**: Testing framework
- **mypy**: Static type checking
- **ruff**: Fast Python linter
- **bandit**: Security linter

### JavaScript/TypeScript Stack
- **Phaser**: 2D game framework
- **Babylon.js**: 3D game engine
- **Vite**: Fast build tool and dev server
- **Jest**: Testing framework
- **ESLint**: JavaScript linter
- **TypeScript**: Type-safe JavaScript

### Infrastructure
- **Docker**: Development environment containerization
- **GitHub Actions**: CI/CD automation
- **VS Code Dev Containers**: Consistent dev environment

## Current Experiments

### Active
- **vampire_survivors** (PR #2): Python/Pygame implementation

### Planned
- **vampire_survivors_web**: Phaser.js port for web browsers
- **ninja_3d**: Babylon.js 3D action game
- **canvas_shooter**: Vanilla HTML5 Canvas experiment

## Best Practices by Technology

### Python/Pygame
- Use sprite groups for efficient collision detection
- Implement game states as separate classes
- Profile performance with cProfile

### Phaser.js
- Use texture atlases to reduce draw calls
- Implement object pools for bullets/enemies
- Leverage Phaser's built-in physics engines

### Babylon.js
- Use LOD (Level of Detail) for performance
- Implement frustum culling
- Optimize mesh instances for repeated objects

### General Web Games
- Minimize asset sizes (compress images, audio)
- Implement progressive loading
- Use Web Workers for heavy computations