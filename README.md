# Ashen Realms: A Console-Based Political RPG Simulation

Ashen Realms is a C++ console RPG where your choices shape your **Reputation** and **Suspicion** as you explore an 8×8 world map, survive combat encounters, and navigate political events in villages and castles.

---

## Features

- **World Map Exploration (8×8):** Move across tiles that represent locations and dangers.
- **Political Event System:** Village and Castle events with 3-choice decisions that affect:
  - Reputation (world trust)
  - Suspicion (guard attention)
  - Gold (rewards or costs)
- **Turn-Based Combat:** Fight enemies that scale with player level.
- **Inventory System:** Collect items and use **Health Potions** to heal.
- **Save/Load System:** Persist your run in `save.txt`.
- **Leaderboard:** Top scores saved to `leaderboard.txt`.

---

## Controls

### Main Menu
- `1` New Game
- `2` Load Game
- `3` Leaderboard
- `4` Quit

### In-Game
- `W` / `A` / `S` / `D` — Move
- `I` — Open inventory (option to use a potion)
- `X` — Save game
- `Q` — Quit (auto-saves + records leaderboard entry)

---

## Map Tiles

| Tile | Meaning |
|------|---------|
| `P`  | Player |
| `.`  | Empty plains (nothing happens) |
| `V`  | Village (political events) |
| `C`  | Castle (political events) |
| `F`  | Forest (combat or rest) |
| `R`  | Ruins (gold / trap / artifact) |
| `E`  | Enemy camp (combat) |

---

## Political System (Reputation & Suspicion)

Your political standing is tracked using:

- **Reputation**: how much people trust you (can range down to -100 and up to 100)
- **Suspicion**: how closely guards watch you (0 to 100)

Some events are gated:
- **Restricted events** require **Reputation > 40** and **Suspicion < 30**
- **Secret missions** require **Reputation > 70** and **Suspicion < 20**

Lose condition:
- If **Suspicion reaches 100**, you are arrested (Game Over).

---

## Combat

Combat is turn-based with options to:
1. Attack  
2. Defend (reduces incoming damage)  
3. Flee (50% chance)  
4. Use Potion  

Winning combat rewards:
- Gold
- Reputation
- XP (leveling improves stats)

---

## Winning

Current win condition in the main game loop:
- **Reputation ≥ 80** AND **Turns Played ≥ 20**

(You can also see an additional “hasWonGame” condition in code, but the loop currently uses the rule above.)

---

## Save Files

This game writes plain-text files in the same folder as the executable:

- `save.txt` — current player save
- `leaderboard.txt` — top scores (max 5)

---

## Build & Run (C++)

### Example (g++)
Compile all `.cpp` files together:

```bash
g++ -std=c++11 -o AshenRealms Dext.cpp player.cpp world_map.cpp combat.cpp politics.cpp save_system.cpp
./AshenRealms
```

> Note: `world_map.cpp` uses `system("cls")` and `system("pause")` (Windows).  
> On Linux/macOS you may want to replace `"cls"` with `"clear"` and remove/replace `"pause"`.

---

## Project Structure (Key Files)

- `Dext.cpp` — Main game loop + menu
- `player.h/.cpp` — Player stats, leveling, inventory
- `world_map.h/.cpp` — Map generation, movement, tile checks
- `combat.h/.cpp` — Enemy generation + combat loop
- `politics.h/.cpp` — Political events + reputation/suspicion logic
- `save_system.h/.cpp` — Save/load + leaderboard

---

## Credits

- **Bilal** — Player stats & inventory (`player.*`)
- **Ahmad** — World map system (`world_map.*`)
- **Hadi** — Combat system (`combat.*`)
- **Haris** — Save/load & leaderboard (`save_system.*`)
- **Taimoor** — Political events (`politics.*`)
