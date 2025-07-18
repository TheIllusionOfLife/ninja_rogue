# Migration Guide

## Migrating vampire_survivors to new structure

The vampire_survivors game from PR #2 should be moved to the new directory structure:

### Current Structure (PR #2)
```
vampire_survivors/
├── src/
├── assets/
│   ├── images/
│   └── sounds/
└── README.md
```

### New Structure
```
games/vampire_survivors/
├── src/
├── assets/
│   ├── images/
│   └── sounds/
├── tests/
├── requirements.txt
└── README.md
```

### Migration Steps
1. Move `vampire_survivors/` directory to `games/vampire_survivors/`
2. Create `requirements.txt` with:
   ```
   pygame>=2.5.0
   ```
3. Add tests directory with initial test structure
4. Update paths in any documentation

### Future Considerations
- Consider extracting reusable sprites to `shared/sprites/`
- Document any game-specific design patterns discovered
- Plan for web port using Phaser.js:
  - Evaluate the feasibility of using Phaser.js for the web port
  - Identify key game features that need to be adapted for web compatibility
  - Research and document any limitations or challenges with Phaser.js
  - Create a prototype to test core game mechanics in Phaser.js
  - Develop a timeline and resource plan for the web port