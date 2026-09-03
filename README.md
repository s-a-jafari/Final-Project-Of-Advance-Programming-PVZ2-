# Plants vs. Zombies: Re-Engineered (LibGDX Edition)

[![Java](https://img.shields.io/badge/Java-17%2B-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)](https://openjdk.org/)
[![LibGDX](https://img.shields.io/badge/LibGDX-1.12%2B-red?style=for-the-badge&logo=libgdx&logoColor=white)](https://libgdx.com/)
[![Gradle](https://img.shields.io/badge/Gradle-Build%20Tool-02303A?style=for-the-badge&logo=gradle&logoColor=white)](https://gradle.org/)
[![Platform](https://img.shields.io/badge/Platform-Desktop%20%28LWJGL3%29-blue?style=for-the-badge)](https://www.lwjgl.org/)

An advanced, feature-complete, modular reimplementation of PopCap's **Plants vs. Zombies 2** developed in Java using the **LibGDX** framework[cite: 3]. Featuring an authentic runtime animation engine for native `.PAM` assets[cite: 3], real-time online and couch multiplayer, rich world hazards, a Zen Garden economy, multi-phase boss fights[cite: 9], and classic mini-games[cite: 19].

---

## 📸 Visual Showcase & Media Gallery

### 🗺️ Hub, Navigation & Almanac
| Main Menu | World Map Selection | Plant Almanac & Filters |
| :---: | :---: | :---: |
| ![Main Menu](image/main_menu.JPG) <br> *Main hub, profile badge, and navigation* | ![World Map](image/chapter_select.JPG) <br> *Chapter selection with unlocked progress* | ![Almanac Plants](image/almanac_plants.JPG) <br> *Plant stats, animations, and family filters* |

| Zombie Almanac | In-Game Shop & Offers | Greenhouse (Zen Garden) |
| :---: | :---: | :---: |
| ![Almanac Zombies](image/almanac_zombies.JPG) <br> *Detailed zombie stats & animations* | ![Shop](image/shop.JPG) <br> *Seed packets, gems, and daily offers* | ![Greenhouse](image/greenhouse.JPG) <br> *3x4 pot grid, growth timers & plant boosts* |

### ⚔️ Battlegrounds & World Hazards
| Ancient Egypt | Dark Ages | Frostbite Caves |
| :---: | :---: | :---: |
| ![Ancient Egypt](image/egypt_gameplay.JPG) <br> *Dynamic sandstorms carrying mummies forward* | ![Dark Ages](image/dark_ages_gameplay.JPG) <br> *Nocturnal battle with tombstone necromancy* | ![Frostbite Caves](image/frostbite_gameplay.JPG) <br> *Freezing winds, ice blocks, and slider tiles* |

| Big Wave Beach | Dr. Zomboss Encounter | Travel Log & Quests |
| :---: | :---: | :---: |
| ![Big Wave Beach](image/beach_gameplay.JPG) <br> *Dynamic water tide and Lily Pad placement* | ![Zomboss Battle](image/zomboss_battle.JPG) <br> *Level 4 boss fight with conveyor belt & HP bar* | ![Travel Log](image/travel_log.JPG) <br> *Daily and regular quest milestones* |

### 🎳 Mini-Games & Multiplayer
| Vasebreaker | Wallnut Bowling | I, Zombie (Multiplayer & Emotes) |
| :---: | :---: | :---: |
| ![Vasebreaker](image/vasebreaker.JPG) <br> *Break mystery vases and battle Gargantuars* | ![Wallnut Bowling](image/wallnut_bowling.JPG) <br> *Roll explosive and giant nuts behind the red line* | ![I Zombie PvP](image/izombie_pvp.JPG) <br> *Online PvP with real-time emoji & sticker drawer* |

| Configuration & Settings | Player Leaderboards |
| :---: | :---: |
| ![Settings](image/settings_modal.JPG) <br> *Speed (1x-3x), difficulty, and audio controls* | ![Leaderboard](image/leaderboard_modal.JPG) <br> *Player rankings sorted by mini-games & quests* |

---

## 🌟 Core Features

### 1. Dynamic World Mechanics & Environmental Hazards
Each chapter introduces unique tile interactions and real-time environmental hazards:
* **Ancient Egypt:** High-velocity sandstorms teleport zombies deep into lawn defenses, accompanied by hieroglyphic gravestones that block direct projectile lanes[cite: 8].
* **Dark Ages:** Sun does not fall from the sky[cite: 8]. Gravestones can spawn Sun, Plant Food, or summon undead legions (`Necromancy`) upon reaching the final wave[cite: 8].
* **Frostbite Caves:** Periodic freezing winds chill plants in stages until fully frozen[cite: 8]. Floating ice slider tiles redirect zombie lane paths, while flying threats like the Dodo Rider bypass ground slides entirely.
* **Big Wave Beach:** Dynamic water tidelines fluctuate across the board. Low-tide zombie ambushes spawn behind defense lines, requiring strategic deployment of Lily Pads[cite: 8].

### 2. Multi-Phase Boss Encounters (Dr. Zomboss)
* Triggered on **Level 4** of each campaign chapter[cite: 9].
* Uses a dedicated **Conveyor-Belt Delivery System**, eliminating the standard sun economy in favor of quick decision-making[cite: 7, 9].
* Boss-specific HUD with a dedicated boss health meter, custom defeat animations, and phase progression[cite: 9].

### 3. Mini-Games
* 🏺 **Vasebreaker:** Break mystery vases containing either defensive plants or dangerous zombies. Plan ahead before cracking open Gargantuar vases!
* 🎳 **Wallnut Bowling:** Defend your lawn behind the red line by rolling regular nuts, high-density heavy nuts, and explosive nuts into incoming waves[cite: 19]. Fully responsive to user speed multipliers[cite: 19].
* 🧠 **I, Zombie (Online & Couch Play):** Turn the tables by commanding the zombie horde!
  * **Online Matchmaking:** Real-time socket-based matchmaking and direct challenge system.
  * **Interactive Reaction Drawer:** Send dynamic pop-up text messages, animated stickers, and emoji reactions during live matches.
  * **Couch Play Mode:** Local two-player mode on a single machine.

### 4. Zen Garden & Metagame Economy
* **Greenhouse (3x4 Plot Grid):** Unlock pots, plant seeds, speed up cultivation using gems, and harvest coin payouts or combat battle-boosts.
* **Collection & Almanac:** View animated sprites, family classes (`PlantCategory`), base HP, damage, and projectile behaviors. Includes a multi-dimensional filter system (by Family, Lock Status, and Upgradability).
* **In-Game Store & Daily Deals:** Purchase seed packets, additional pots, and plant food upgrades via coins and gems.
* **Quest Log & Leaderboard:** Track and claim daily/lifetime achievements with local and remote user ranking tables.

---

## 🏗️ Technical Architecture

The project follows a clean, decoupled **Model-View-Presenter (MVP) / Model-View-Controller (MVC)** architectural design:


```

com.test1.PlantsVsZombies.src/
├── Audio/                      # SoundManager (SFX & BGM streams)
├── Enums/                      # Strong typing (ChapterType, PlantType, ZombieType, etc.)
├── Menu/                       # Screen controllers & presenter logic
├── Model/
│   ├── ChaptersAndLevels/      # Campaign chapter configurations and level loaders
│   ├── GamePlayType/           # Core match engines (Simple, ConveyorBelt, Zomboss, SaveOurSeeds, etc.)
│   ├── Greenhouse/             # Zen garden timer and growth simulation
│   ├── MiniGames/              # Game rules for Vasebreaker, Bowling, and I, Zombie
│   ├── PlantsAndZombies/       # Entities, Projectiles, Animations, and Factories
│   ├── Quests/                 # Quest tracking and daily resets
│   ├── Shop/                   # Store inventory and daily offer generators
│   └── User/                   # Authentication, user progress serialization, and security
├── Network/                    # Async client-server TCP sockets & push listeners
└── View/
├── LibGDXViews/            # LibGDX Screens, World/HUD Renderers, Scene2D Stage modals
└── ViewInterfaces/         # Decoupled UI contracts

```

### Key Technical Highlights
* **Fixed-Step Simulation vs. Render Interpolation:** Game logic runs on a deterministic tick accumulator (`TICK_RATE = 0.1f`), while graphics render at monitor refresh rates with delta-time interpolation[cite: 3].
* **Native PAM Animation Player:** Fully custom vector/sprite PAM interpreter (`PamPlayer`) reading official animation states, clips, and layer visibilities[cite: 3].
* **Robust Concurrent Update Loop:** Entity management utilizes reverse indexed iterating and buffer queues (`pendingNewPlants`, `pendingNewZombies`) to completely prevent `ConcurrentModificationException` during mid-frame spawns[cite: 8, 9].
* **Clean State Synchronization:** The `updatePlantTiles()` and `updateZombieTiles()` pipelines ensure entity coordinates and logical grid states stay unified at all times.

---

## 🎮 Controls & Shortcuts

| Input | Action |
| :--- | :--- |
| **Left Mouse Button** | Select card, plant seed packet, collect sun/plant food, break vases[cite: 11] |
| **Right Mouse Button** | Cancel card/shovel selection[cite: 11, 19] |
| **Shovel Button / Click** | Dig up an active plant from the tile[cite: 11] |
| **Plant Food / Drag** | Boost target plant for signature ultimate ability[cite: 11] |
| **Num Keys (1 - 5)** | *(I, Zombie)* Select zombie card from deck |
| **W / S or Up / Down** | *(I, Zombie)* Change active deployment lane |
| **Space / Enter** | *(I, Zombie)* Spawn selected zombie on active lane |
| **Debug Plus Buttons (`+`)** | *(Debug Mode)* Add +100 Sun or +1 Plant Food instant cheat[cite: 11] |

---

## ⚙️ Game Settings & Configuration

Accessible via the in-game Pause menu or Main Menu settings panel[cite: 12]:
* **Game Speed Multiplier:** Toggle between **1x**, **2x**, and **3x** speeds across single-player and mini-games[cite: 19].
* **Difficulty Scaling:** Dynamic difficulty settings (1 to 5) altering zombie waves and health multipliers.
* **Lawn Tile Grid:** Toggle visual red grid boundaries for precision planting.
* **Audio Channels:** Independent volume sliders and mute switches for music and sound effects.

---

## 🚀 Getting Started

### Prerequisites
* **Java Development Kit (JDK):** Version 17 or higher.
* **Gradle:** Version 7.0+ (or use the included wrapper).
* **Display:** Minimum 1280x720 screen resolution (optimized for 1920x1200 virtual viewport)[cite: 3].


### Build and Run

1. **Clone the repository:**
```bash
git clone git@github.com:s-a-jafari/PVZ2_AP-Project.git
```

2. **Verify Asset Directory Structure:**
Ensure assets are placed under the root `assets` directory:
```text
assets/
├── Assets/
│   └── 768/              # PopCap PAM texture atlases and animations
└── pvz.ttf               # Primary TrueType game font

```


3. **Execute using Gradle:**
```bash
# Unix / macOS
./gradlew run

# Windows
gradlew.bat run

```


4. **Build Standalone JAR:**
```bash
./gradlew desktop:dist

```


The executable JAR file will be generated in `desktop/build/libs/`.
