# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**ninja_rogue** - A Python-based game project utilizing AI agents for creative content generation. The project leverages Google's Gemini AI through the `madspark` package namespace. Licensed under Apache 2.0.

## Repository Structure

```
ninja_rogue/
├── src/madspark/          # Main package namespace
│   ├── agents/           # AI agent modules
│   │   ├── idea_generator.py
│   │   ├── critic.py
│   │   ├── advocate.py
│   │   └── skeptic.py
│   ├── core/             # Core functionality
│   │   └── coordinator.py
│   └── utils/            # Utilities and constants
│       └── constants.py
├── config/
│   └── requirements.txt  # Python dependencies
├── .devcontainer/        # VS Code dev container setup
└── .github/workflows/    # CI/CD pipelines
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

### Development Workflow
```bash
# Run tests (when implemented)
pytest

# Type checking
mypy src/

# Linting
ruff check src/

# Security scanning
bandit -r src/

# Install dependencies
pip install -r config/requirements.txt
```

### Python Environment
- **Supported Versions**: Python 3.10-3.13
- **Package Manager**: pip
- **Virtual Environment**: Handled by devcontainer

## Architecture Notes

### AI Agent System
The project implements a multi-agent creative system with specialized roles:

1. **Idea Generator** (`src/madspark/agents/idea_generator.py`)
   - `generate_ideas()`: Creates new game concepts/features
   - `build_generation_prompt()`: Constructs prompts for idea generation

2. **Critic** (`src/madspark/agents/critic.py`)
   - `evaluate_ideas()`: Evaluates generated ideas critically

3. **Advocate** (`src/madspark/agents/advocate.py`)
   - `advocate_idea()`: Champions and defends ideas

4. **Skeptic** (`src/madspark/agents/skeptic.py`)
   - `criticize_idea()`: Provides constructive criticism

5. **Coordinator** (`src/madspark/core/coordinator.py`)
   - Orchestrates agent interactions

### Key Principles
- **KISS**: Keep It Simple, Stupid
- **DRY**: Don't Repeat Yourself  
- **YAGNI**: You Aren't Gonna Need It
- **SOLID**: Single responsibility, Open/closed, etc.
- **TDD**: Test-Driven Development approach
- **Boy-Scout Rule**: Leave code cleaner than found

## Testing

### Test Structure
```bash
# Run all tests
pytest

# Run specific test file
pytest tests/test_agents.py

# Run with coverage
pytest --cov=src/madspark

# Run specific test
pytest tests/test_agents.py::test_idea_generator
```

### CI/CD Pipeline
- **Multi-version Testing**: Python 3.10-3.13
- **Automated Checks**: Linting, type checking, security scanning
- **PR Reviews**: Automated Claude AI code reviews on pull requests

## Development Guidelines

1. **Always create feature branches** - Never commit directly to main
2. **Follow conventional commits** - Use prefixes like `feat:`, `fix:`, `test:`
3. **Write tests first** - TDD approach for all new features
4. **Mock external dependencies** - Especially Google GenAI calls in tests
5. **Use type hints** - All functions should have proper type annotations

## External Dependencies

- **Google Generative AI**: Primary AI backend (requires API key)
- **Docker**: Development environment containerization
- **GitHub Actions**: CI/CD automation

## Environment Variables

Set these in your development environment:
- `PYTHONPATH`: Should include `src` directory
- `GEMINI_API_KEY`: Required for Google GenAI functionality (not needed for basic development)