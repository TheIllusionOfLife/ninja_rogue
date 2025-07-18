# Shared Resources

This directory contains assets and utilities that can be shared across multiple game implementations.

## Structure

- `sprites/` - Reusable sprite assets (with proper licensing)
- `sounds/` - Common sound effects and music
- `utils/` - Shared utility functions and classes

## Usage Guidelines

1. Only put truly reusable assets here
2. Document licensing for all assets
3. Keep utilities technology-agnostic when possible
4. If utilities are technology-specific, organize in subdirectories:
   - `utils/python/`
   - `utils/javascript/`

## Asset Licensing

Always document the source and license of shared assets:
- Create a `LICENSE.txt` file in each asset directory
- Credit original authors
- Ensure licenses are compatible with Apache 2.0