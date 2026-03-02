# Antigravity Game Dev Stack

## 1. Engine Selection Philosophy
* **Learning / Prototyping:** `Pygame CE` (Community Edition).
    * *Why:* Logic transparency. usage of raw loops forces understanding of frame timing and state management.
* **Indie Production:** `Godot 4.x` (GDScript).
    * *Why:* Open source, lightweight, node-based architecture fits the "Composition over Inheritance" mental model.

## 2. The Game Loop Protocol (Pygame)
Every game must adhere to the **D.U.R.** Loop to ensure clean code separation:
1. **Delta:** Calculate `dt` (delta time) at the start of the frame.
2. **Update:** Update game logic (movement, physics) using `dt`. **NO DRAWING HERE.**
3. **Render:** Clear screen, draw all entities, flip display. **NO LOGIC HERE.**

### Pattern:
```python
while running:
    # 1. Delta
    dt = clock.tick(60) / 1000.0
    
    # 2. Update
    handle_input()
    player.update(dt)
    
    # 3. Render
    screen.fill(COLORS.BG)
    player.draw(screen)
    pygame.display.flip()
```

## 3. Golden Scaffold (Godot Style)
```text
project_name/
├── assets/
│   ├── sprites/
│   ├── audio/
│   └── fonts/
├── scenes/                # Levels or Menus (.tscn)
├── scripts/               # Logic files (.gd)
│   ├── entities/          # Player.gd, Enemy.gd
│   ├── globals/           # GameState.gd
│   └── ui/                # HUD.gd
└── project.godot
```

## 4. Asset Management
* **Structure:**
    * `/assets/sprites` - PNGs only.
    * `/assets/audio/sfx` - WAV (short sounds).
    * `/assets/audio/music` - OGG (looping tracks).
    * `/assets/fonts` - TTF/OTF.
* **Loading:**
    * Pre-load assets into a `ResourceHandler` dictionary at startup. Never load files inside the game loop.

## 5. Coding Standards
* **Vectors:** Always use `pygame.math.Vector2` for positions/velocities. Never use separate `x, y` variables.
* **Classes:** Every major entity (Player, Enemy) inherits from `pygame.sprite.Sprite`.
