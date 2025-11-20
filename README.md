# Lost Bunny: Journey Home
## A 2D Adventure Game Engine with Tilemap Editor

**[Watch Beta Progress Video](https://youtu.be/W3CKqiKC-jA)**

### Project Overview
Lost Bunny is a story-driven 2D adventure game where you play as a pet bunny that has been hit by a car and finds itself in the spirit realm. Your goal is to navigate through three mystical levels, and find your way back to your body in the real world before it's too late.

## Compilation Instructions

### Prerequisites
- D compiler (DMD or LDC2)
- DUB (D package manager)
- SDL3 library installed on your system

### Building the Game
```bash
cd Engine
dub build --config=application
./lostbunny
```

### Building the Tilemap Editor
```bash
cd Engine/Editor
dub build --config=editor
./tilemap_editor
```

## Game Controls

### Menu
- **Arrow Keys / W/S** - Navigate menu options
- **Enter / Space** - Select menu option

### In-Game
- **Right & Left Arrow Keys / WD** - Move the bunny
- **Up Arrow / Space / A** - Jump
- **ESC** - Return to menu

## Tilemap Editor

The tilemap editor is a standalone tool for creating game levels.

### Tile Types
- **0**: Empty (no tile)
- **1**: Tile (platform block)
- **2**: Spike Up (pointing upward)
- **3**: Spike Right (pointing right)
- **4**: Spike Down (pointing downward)
- **5**: Spike Left (pointing left)
- **6**: Carrot (collectible)

### Using the Tilemap Editor

#### Building
```bash
# Build the tilemap editor
dub build --config=editor

# Build the main game
dub build --config=application
```

#### Running the Editor
```bash
./tilemap_editor
```

#### Editor Controls
- **Q-E**: Select level (1-3)
- **0-6**: Select tile type (shown in the right panel)
- **Left Click**: Place selected tile
- **Right Click**: Erase tile
- **S**: Save tilemaps to `assets/tilemaps/lostbunny_level1.json`, `assets/tilemaps/lostbunny_level2.json`, `assets/tilemaps/lostbunny_level3.json`
- **L**: Load tilemaps from `assets/tilemaps/lostbunny_level1.json`, `assets/tilemaps/lostbunny_level2.json`, `assets/tilemaps/lostbunny_level3.json`
- **C**: Clear entire tilemap
- **ESC**: Quit editor

### Tilemap File Format
20x15 grid (640x480 pixels at 32px per tile)
```json
{
  "width": 20,
  "height": 15,
  "tileSize": 32,
  "tiles": [
    [0, 0, 0, ...],
    [0, 1, 1, ...],
    ...
  ]
}
```

### Level Design Tips
1. **Start Platform**: Place tiles (1) at the bottom left for bunny spawn point (starts at x=60, y=350)
2. **Goal Platform**: Place tiles at the right side (around x=540-600) for the win condition
3. **Vertical Walls**: Stack single tiles vertically for wall-jumping sections
4. **Spike Placement**: 
   - Use Spike Up (2) on top of horizontal platforms
   - Use Spike Left (5) or Right (3) on vertical walls for "growing" effect
   - Use Spike Down (4) for ceiling spikes
5. **Carrots**: Place carrots (6) around the level for collectibles
6. **Bottom Border**: You can place Spike Up (2) tiles along the bottom row (row 14) to create a spike floor, or leave it open for an instant-death pit

### Workflow
1. Run `./tilemap_editor`
2. Design your level using the editor
3. Press **S** to save
4. Run `./lostbunny` to play your custom level!
