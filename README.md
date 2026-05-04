# Game Folder Blueprint

A clean, scalable folder structure template for game development projects.  
Compatible with any engine (Unity, Godot, Unreal) or custom frameworks.  
Keep your code, assets, documentation, and builds organized from day one.

## Recommended Structure
## Folder Structure

```text
project/
├─ assets/              # All raw game assets
│  ├─ models/           # 3D models (FBX, glTF, blend, etc.)
│  ├─ audio/            # Music, sound effects, voice lines
│  ├─ fonts/            # Font files
│  ├─ shaders/          # Custom shaders (HLSL, GLSL, Godot shaders)
│  └─ textures/         # Images, sprites, UI textures, normal maps
│
├─ docs/                # Game design documents, technical specs, references
│
├─ tools/               # External helper scripts (build pipelines, asset converters, etc.)
│
├─ scenes/              # Engine-specific scene files (Unity, Godot, Unreal)
│  ├─ character/        # Scenes for player / NPC characters
│  └─ levels/           # Level / map scenes
│
├─ blender/             # Source Blender files (.blend) for models, animations, or level blocking
│
├─ src/                 # Source code (scripts)
│  ├─ Ai/               # Artificial intelligence systems
│  │  ├─ Detection/     # Vision, hearing, awareness logic
│  │  └─ StateMachine/  # Finite state machines, behavior trees
│  ├─ Core/             # Core systems (game loop, managers, singletons)
│  ├─ Input/            # Input handling, controller mappings, rebinding
│  ├─ Player/           # Player-specific logic
│  │  └─ Inventory/     # Inventory management, items, equipment
│  ├─ Ui/               # User interface
│  │  └─ Hud/           # Heads-up display elements (health, ammo, minimap)
│  ├─ World/            # World / level logic
│  │  └─ Interactables/ # Doors, levers, pickups, triggers
│  └─ Combat/           # Combat mechanics (damage, weapons, abilities)
│
├─ resources/           # Runtime data files (non-code, non-raw assets)
│  ├─ environments/     # Environment data (lighting presets, weather profiles)
│  └─ materials/        # Material instances, physics materials
│
└─ README.md            # You are here
```

## Folder Descriptions

| Folder | Purpose |
|--------|---------|
| `assets/` | All imported/raw media – models, audio, fonts, shaders, textures. Keep source files here. |
| `docs/` | Design documents, GDD (Game Design Document), style guides, research. |
| `tools/` | Scripts and small applications that help development (e.g., sprite packer, dialogue compiler). |
| `scenes/` | Engine scene files. Subfolders help separate characters from level scenes. |
| `blender/` | Source Blender files. Useful for iterating on 3D assets without polluting `assets/models`. |
| `src/` | All game code. Organized by feature (AI, Core, Input, Player, UI, World, Combat). |
| `resources/` | Runtime data files (JSON, XML, binary) that configure environments, materials, or other game systems. |


## Folder Details

### `assets/`
All non‑code content that will be packaged into the final game. Keep it organized by type (graphics, audio) and optimize files (compression, resolution) before committing.

### `scripts/`
Source code split by responsibility. Avoid giant files – prefer small, reusable modules.

### `scenes/` and `levels/`
- **scenes/**: Used in engines that work with scenes (Unity, Godot, Unreal). Each scene file represents a game state (menu, level, game over).
- **levels/**: Level data in a serializable format (e.g., JSON). Allows editing levels without touching code.

### `builds/`
Generated builds (Windows, Linux, Web, etc.). **Do not version this folder** – add it to `.gitignore`.

### `docs/`
Living documentation. Include an internal `README` in each subfolder. Keep the GDD up to date.

### `tests/`
Automated tests. For games, focus on logic tests (combat systems, inventory) and input simulations.

### `tools/`
Auxiliary tools: sprite sheet packers, dialogue generators, build pipelines. These are scripts executed outside the game.

### `config/`
Configuration files (controls, volume, graphics quality). In multiplayer games, some may be client‑side.


## How to Use This Blueprint

1. **Create the folder tree** inside your game project root.
2. **Adjust to your engine** – For example, Unity expects `Assets/` at the root; you can merge `assets/` into `Assets/`, or keep this structure as a guide inside `Assets/`.
3. **Set up `.gitignore`** to exclude builds, temporary files, and engine caches (see example below).
4. **Add a `README` inside subfolders** if they need special instructions (e.g., how to export models from Blender).


## Customizing for Your Project
* Smaller project? – Combine src/Combat and src/Player if combat is player‑only.
* Multiplayer? – Add src/Network/ and split Core/ into client/server managers.
* 2D game? – Rename assets/textures/ to assets/sprites/ and skip assets/models/.

## Example `.gitignore`

```gitignore
# Builds
/builds/
*/builds/

# Engine caches
[Ll]ibrary/
[Tt]emp/
[Oo]bj/
.vscode/
.idea/

# Blender backups
*.blend1
*.blend2

# OS metadata
.DS_Store
Thumbs.db