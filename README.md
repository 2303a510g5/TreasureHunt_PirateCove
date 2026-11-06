<div align="center">

# 🏴‍☠️ Treasure Hunt: Pirate Cove

### A pirate-era 3D endless runner built in Unity

![Unity](https://img.shields.io/badge/Unity-6000.x-black?logo=unity)
![Language](https://img.shields.io/badge/C%23-scripts-239120?logo=csharp&logoColor=white)
![Genre](https://img.shields.io/badge/genre-endless%20runner-b8862b)
![Platform](https://img.shields.io/badge/platform-Windows%20(PC)-blue)
![Status](https://img.shields.io/badge/status-in%20development-orange)

*Run the pier, grab the gold, dodge the hazards, and stay ahead of the pirates on your tail.*

</div>

---

## 📑 Table of Contents
- [About the Game](#-about-the-game)
- [Screenshots](#-screenshots)
- [Features](#-features)
- [Controls](#-controls)
- [Gameplay Guide](#-gameplay-guide)
- [Getting Started](#-getting-started)
- [Project Structure](#-project-structure)
- [How It Works](#-how-it-works)
- [Roadmap](#-roadmap)
- [Team](#-team)
- [Acknowledgements](#-acknowledgements)
- [License](#-license)

---

## 🎮 About the Game

**Treasure Hunt: Pirate Cove** is a 3D endless runner set in the golden age of piracy. You play a treasure hunter sprinting down a wooden pier through Pirate Cove. Pirate ships sail alongside, firing cannons into the sea, while a crew of cutlass-wielding pirates chases you from behind. Collect gold coins and treasure chests, grab stars, jump or sidestep hazards, and survive as long as you can. Every hit lets the pirates close in, and with no lives left, they catch you.

The project was created as a university game-development project at **SR University** (School of Computer Science and Artificial Intelligence).

---

## 🖼️ Screenshots

<img width="1087" height="508" alt="WhatsApp Image 2026-11-06 at 1 07 23 PM" src="https://github.com/user-attachments/assets/32df15dc-44b9-4ab4-8b44-293a0e38f4bd" />


---

## ✨ Features

- **3D endless runner** on a three-lane wooden pier with smooth lane switching and jumping
- **Pirate-themed world**: pirate galleons with cannon fire, treasure islands, Skull Rock on the horizon, rope rails, lanterns, Jolly Roger flags, sunset sky and sea haze
- **Chasing pirates** who close in each time you lose a life and catch you when your lives run out
- **Treasure to collect**: gold coins (including arcs over obstacles), treasure chests and stars
- **Varied hazards**: barrels, spikes, crates and cannons (jump them), plus crate stacks (change lane)
- **Health system**: 3 lives with a short invulnerability window after every hit
- **4 levels** with rising speed and obstacle density; finish a level to unlock the next and earn up to 3 stars
- **Missions and achievements** that track your progress across runs
- **Full menu system**: Play, Levels, Missions, Achievements, Settings, Quit
- **In-game screens**: HUD (lives, coins, stars, distance), Pause, Game Over, Level Complete
- **Settings**: music and SFX volume sliders, graphics quality switch
- **Procedural audio**: sound effects and a looping tune are generated in code, so no audio files are needed
- **Progress saving** using Unity `PlayerPrefs`
- **One-click scene builder**: an editor tool builds the prefabs, scenes and UI automatically

---

## ⌨️ Controls

| Action | Keyboard |
|---|---|
| Move left / right (switch lane) | `A` / `D` or `←` / `→` |
| Jump | `Space`, `↑` or `W` |
| Pause / resume | `Esc` or `P` |
| Restart after Game Over | `R` or `Enter` |

> Touch / mobile controls are planned (see the [Roadmap](#-roadmap)).

---

## 🧭 Gameplay Guide

**Goal:** reach the distance target for the level while collecting as much treasure as you can.

| Item | Effect |
|---|---|
| 🪙 Gold coin | +10 coins |
| 🧰 Treasure chest | +50 coins and counts toward the *Find Treasure Chests* mission |
| ⭐ Star | 5 stars appear in each level; they decide your level rating |
| 🛢️ Barrel / 🪤 Spikes / 📦 Crate / 💣 Cannon | Lose 1 life. They can be jumped over |
| 🧱 Crate stack | Lose 1 life. Too tall to jump, so change lane |

**Levels**

| Level | Distance target | Notes |
|---|---|---|
| 1 | 500 m | Gentle start |
| 2 | 1000 m | Faster, more obstacles |
| 3 | 1500 m | Faster still |
| 4 | 2000 m | Hardest |

Speed rises steadily during a run. Finishing a level unlocks the next one. Your rating is 3 stars for collecting all 5 stars, 2 stars for 3 or more, and 1 star otherwise.

**Missions:** collect 100 coins · find 3 treasure chests · run 500 meters
**Achievements:** Coin Collector (1000 coins) · Treasure Hunter (10 chests) · Marathon Runner (5000 meters)

---

## 🚀 Getting Started

### Requirements
- [Unity Hub](https://unity.com/download) and **Unity 6 (6000.x)**
- Windows (PC build target)

### Run the project
1. Clone the repository:
   ```bash
   git clone https://github.com/<your-username>/<your-repo-name>.git
   ```
2. Open **Unity Hub → Add → Add project from disk** and select the cloned folder.
3. Open it with Unity 6 and let it import.
4. If TextMeshPro asks, choose **Import TMP Essentials** (or go to *Window → TextMeshPro → Import TMP Essential Resources*).
5. Open `Assets/Scenes/MainMenu.unity` and press **Play**.

### Rebuild the scenes (optional)
If scenes or prefabs are missing or broken:

1. Go to **Pirate Cove → Build Entire Game** in the menu bar and click **Build**.
2. This recreates the tags, materials, prefabs, the `MainMenu` and `Game` scenes, and the Build Settings list.

### Build an executable
**File → Build Profiles** (or *Build Settings*) → **Windows** → **Build**. Share the whole output folder, not just the `.exe`.

### Reset saved progress
In the editor: **Edit → Clear All PlayerPrefs**.

---

## 📁 Project Structure

```
Assets/
├── Editor/
│   └── PirateCoveBuilder.cs     # One-click builder for prefabs, scenes and UI
├── Scenes/
│   ├── MainMenu.unity
│   └── Game.unity
├── Scripts/
│   ├── RunnerGame.cs            # Game state, lives, score, HUD, pause / game over / level complete
│   ├── RunnerPlayer.cs          # Lane switching, jumping, collision handling
│   ├── TrackSpawner.cs          # Endless pier: obstacles, coins, chests, stars, islands
│   ├── PirateChasers.cs         # Pirates that run behind the player
│   ├── RunAnimator.cs           # Arm / leg swing animation
│   ├── Pickup.cs                # Coins, chests, stars
│   ├── ShipCannons.cs           # Decorative cannon fire from ships
│   ├── CannonBall.cs / SplashFx.cs
│   ├── FollowPlayer.cs / FollowZ.cs / CameraFollow.cs
│   ├── MenuUI.cs                # Main menu, levels, missions, achievements, settings
│   ├── Save.cs                  # Saved progress and level settings
│   ├── AudioManager.cs          # Procedurally generated sound effects and music
│   └── GameInput.cs             # Keyboard input (legacy and new Input System)
├── Materials/  Prefabs/         # Generated by the builder
Packages/
ProjectSettings/
```

---

## ⚙️ How It Works

- **Endless track:** `TrackSpawner` spawns 20 m pier segments ahead of the player and destroys old ones behind. Each segment is filled with obstacles, coin trails (weighted toward the middle lane), chests and stars. It never blocks all three lanes at once.
- **Player:** `RunnerPlayer` moves forward at the game speed and switches between three lanes. Jumping uses simple custom gravity. Collisions use trigger colliders and tags (`Hazard`, `Collectible`).
- **Difficulty:** `Save.cs` defines each level's target distance, start speed and obstacle chance. Speed increases gradually during a run.
- **Chasers:** `PirateChasers` keeps the pirates behind the player. Their distance depends on your remaining lives.
- **Scenery:** ships, Skull Rock and islands follow the player so the world always feels full.
- **Persistence:** coins, chests, distance, unlocked levels, level stars and volume settings are saved with `PlayerPrefs`.

---

## 🗺️ Roadmap

- [ ] Touch / mobile controls
- [ ] Gaps in the pier to jump over
- [ ] Imported 3D character and environment models (replace the primitive shapes)
- [ ] Power-ups (shield, coin magnet)
- [ ] Slide move and more obstacle types
- [ ] Local high-score table
- [ ] Additional levels and environments

---

## 👥 Team

| Name | Role |
|---|---|
| **S. Sathwika** | Developer |
| **S. Sharanya** | Developer |

**Institution:** SR University, Ananthasagar, Warangal, Telangana
**Program:** B.Tech, School of Computer Science and Artificial Intelligence (2026–2027)
**Faculty guide:** *[Faculty Guide Name]*

---

## 🙏 Acknowledgements

- [Unity Technologies](https://unity.com/) for the game engine
- Our faculty guide and **SR University** for their guidance and support

---

## 📄 License

This project was created for academic purposes. Choose a license that suits you (for example [MIT](https://choosealicense.com/licenses/mit/)) and add a `LICENSE` file to the repository.
