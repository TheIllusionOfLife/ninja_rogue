# Ninja Rogue

An experimental game development repository exploring various technologies and frameworks for creating action/survival games.

## Overview

This repository serves as a testing ground for game development across multiple technologies. Each game implementation is self-contained in its own directory, allowing for experimentation with different frameworks, languages, and approaches.

## Technology Stack Exploration

Currently experimenting with:
- **Python/Pygame** - Desktop game development, rapid prototyping
- **Phaser.js** - 2D web games with extensive features
- **Babylon.js** - 3D web games with WebGL
- **HTML5 Canvas** - Lightweight web games with vanilla JavaScript
- **Godot** - Cross-platform game engine (future consideration)

## Repository Structure

```
ninja_rogue/
├── games/
│   ├── vampire_survivors/        # Python/Pygame implementation
│   ├── vampire_survivors_web/    # Phaser.js implementation (planned)
│   └── ninja_3d/                # Babylon.js experiment (planned)
├── shared/                      # Shared assets and utilities
├── docs/                        # Documentation and design notes
└── tools/                       # Development tools and scripts
```

## Development

This project uses VS Code Dev Containers for a consistent development environment.

```bash
# Start development environment
make up

# Open shell in container
make shell

# Start Claude Code AI assistant
make claude
```

### Running Games

#### Python Games
```bash
cd games/[game_name]
pip install -r requirements.txt
python src/main.py
```

#### Web Games (Phaser/Babylon.js)
```bash
cd games/[game_name]
npm install
npm start
```

## Current Experiments

### Active
- **vampire_survivors** - Python/Pygame implementation of a wave-based survival game

### Planned
- **vampire_survivors_web** - Port to Phaser.js for web deployment
- **ninja_3d** - 3D action game using Babylon.js
- **canvas_shooter** - Vanilla HTML5 Canvas experiment

## Contributing

When adding a new game experiment:
1. Create a new directory under `games/`
2. Include a README with setup instructions
3. Add technology-specific `.gitignore` entries
4. Document your findings and learnings

## Design Philosophy

- **Experimentation First** - Try different approaches to find what works best
- **Modular Structure** - Each game is independent and self-contained
- **Learn by Doing** - Implement the same game concept in multiple frameworks
- **Share Knowledge** - Document learnings and best practices discovered

## License

Apache 2.0