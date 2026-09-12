<div align="center">

# 🐦 FLAPPY BIRD — UNITY EDITION

> **Tap. Fly. Survive. Beat your high score.**

[![Unity](https://img.shields.io/badge/Unity-5.6+-000000?style=for-the-badge&logo=unity&logoColor=white)](https://unity.com/)
[![C#](https://img.shields.io/badge/C%23-239120?style=for-the-badge&logo=c-sharp&logoColor=white)](https://docs.microsoft.com/en-us/dotnet/csharp/)
[![Platform](https://img.shields.io/badge/Platform-PC%20%7C%20Mac%20%7C%20Linux-lightgrey?style=for-the-badge)](#)
[![GitHub Repo stars](https://img.shields.io/github/stars/svk-vasanthkumar/Flappy-Bird-Game-Unity?style=for-the-badge&color=e3b341)](https://github.com/svk-vasanthkumar/Flappy-Bird-Game-Unity/stargazers)

*A classic, endless arcade flying challenge rebuilt from the ground up using Unity and C#.*

*(Replace this placeholder with a gameplay GIF)*
![Game Preview](https://via.placeholder.com/600x338.png?text=Gameplay+Preview+.GIF+Here)

</div>

---

## 🌤️ About The Game

This project is a Unity-based recreation of the classic arcade hit, Flappy Bird. The objective is simple: navigate a flying bird through a continuous, procedurally generated obstacle course of pipes without colliding. The game features real-time physics, dynamic score tracking, state management, and infinite procedural generation. 

It serves as a comprehensive example of 2D game development in Unity, emphasizing clean component-based architecture and robust C# scripting.

---

## ⚡ Quick Summary

| 🎮 **Game** | Flappy Bird Unity Clone |
| :--- | :--- |
| 🛠 **Engine** | Unity (Legacy 5.6+ compatible) |
| 💻 **Language** | C# |
| 🎯 **Genre** | Arcade / Endless Runner |
| 🏆 **Objective** | Survive and score by passing pipes |
| 🐦 **Player** | Physics-driven animated bird |
| ☁️ **Obstacles** | Procedurally spawned pipe columns |
| 🔊 **Audio** | Flight, score, and death SFX |
| 📱 **Input** | Mouse Click / Tap |

---

## 🎯 Gameplay Loop

```text
🐦 FLAP
   ↓
⬆️ RISE
   ↓
🧱 AVOID PIPES
   ↓
🎯 PASS PIPE
   ↓
🏆 +1 SCORE
   ↓
🔁 KEEP FLYING
   ↓
💥 COLLISION
   ↓
🔄 RESTART
```

---

## 🎮 Controls

| Platform | Action | Control |
| :--- | :--- | :--- |
| 🖥️ **PC / Mac** | Flap / Jump | `Left Mouse Click` |
| 📱 **Mobile** | Flap / Jump | `Screen Tap` |
| ⌨️ **Keyboard** | Flap / Jump | `Spacebar` *(if mapped in Input Manager)* |

---

## ⚡ Features

* 🐦 **Physics-Based Flight:** Real-time gravity and velocity manipulation.
* 🧱 **Infinite Level Generation:** Procedural and continuous pipe spawning.
* 🎯 **Dynamic Scoring:** Triggers detect successful pipe navigation.
* 💥 **State-Driven Gameplay:** Seamless transitions between Intro, Playing, and Dead states.
* 🎬 **Sprite Animation:** Unity Animator drives bird flapping states.
* 🌍 **Parallax Environment:** Moving floor and background elements.
* 🔊 **Integrated Audio:** Sound effects triggered by gameplay events.

---

## 🧠 Game Architecture

The project relies on a decoupled, component-based architecture where individual scripts handle specific gameplay responsibilities, managed by a central game state.

```text
                 🎮 GAMEPLAY LOOP
                        │
          ┌─────────────┼─────────────┐
          │             │             │
        PLAYER       SPAWNER        SCORE
          │             │             │
          ▼             ▼             ▼
    FlappyScript      Pipes      ScoreManager
          │             │             │
          ▼             ▼             ▼
      Collision ◄───► Triggers ◄── UI Updates
          │
          ▼
      GameState (Intro ➔ Playing ➔ Dead)
```

---

## 🛠️ C# Script Breakdown

The codebase is modular, keeping physics, scoring, and level generation independent.

| Script | Core Responsibility |
| :--- | :--- |
| `FlappyScript.cs` | Player input, vertical velocity (flap), rotation, and collision detection. |
| `SpawnerScript.cs` | Instantiates pipe prefabs at regular intervals with randomized vertical offsets. |
| `ScoreManagerScript.cs` | Listens for trigger events, increments score, and updates UI. |
| `CameraFollow.cs` | Keeps the viewport locked onto the player's horizontal position. |
| `FloorMoveScript.cs` | Translates the floor sprite to simulate forward momentum. |
| `PipeDestroyerScript.cs`| Garbage collection: destroys off-screen pipes to save memory. |
| `GameState.cs` | Manages the global state (`Intro`, `Playing`, `Dead`, `Restart`). |

---

## 🧩 Unity Components Used

* **Rigidbody2D:** Drives the bird's gravity and jumping physics.
* **Collider2D (Box/Polygon):** Handles solid impacts (pipes/floor) and trigger zones (scoring).
* **Animator:** Transitions the bird's sprite between flapping and falling.
* **AudioSource:** Plays distinct sound clips for flaps, scores, and crashes.
* **SpriteRenderer:** Renders 2D assets with sorting layers.
* **Prefabs:** Allows infinite instantiation of pipe combinations.

---

## 🐦 Player Mechanics

The `FlappyScript.cs` acts as the core controller. 
* **Movement:** The bird maintains a constant horizontal speed.
* **Flapping:** Clicking applies a sudden upward force to the `Rigidbody2D`, counteracting constant gravity.
* **Rotation:** The script adjusts the bird's Z-axis rotation based on its Y-axis velocity (pointing up when rising, nose-diving when falling).
* **Death State:** Hitting a pipe or the floor instantly zeros out horizontal velocity, triggers the death animation/sound, and shifts the `GameState` to `Dead`.

---

## 🏆 Scoring

```text
Enter Trigger Zone (Between Pipes)
               ↓
          +1 SCORE
               ↓
    Update Text UI Element
               ↓
      Compare with BEST SCORE
```

---

## ✨ Animation & 🎨 Visual Style

The game utilizes a classic pixel-art aesthetic. 
* **Animation System:** The `Assets/Animations/` folder contains controllers that swap sprites to simulate wing movement.
* **Environment:** The sky, clouds, and city skyline remain static in the background while the striped floor moves to create a parallax illusion of speed.

---

## 🔊 Audio

Audio cues are essential to the game's feedback loop. The player script calls specific `AudioSource` components upon:
1.  **Flapping:** A quick swoosh sound.
2.  **Scoring:** A positive chime.
3.  **Dying:** A crash/thud sound effect.

---

## 📁 Project Structure

```text
Flappy-Bird-Game-Unity/
│
├── Assets/
│   ├── Animations/      # Animator controllers and clips
│   ├── Prefabs/         # Reusable Pipes and GameObjects
│   ├── Scenes/          # MainGame scene file
│   ├── Scripts/         # C# Source Code
│   ├── Sounds/          # SFX audio files
│   └── Sprites/         # 2D visual assets
│
├── ProjectSettings/     # Unity configuration files
└── README.md            # Project documentation
```

---

## 🚀 How To Run

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/svk-vasanthkumar/Flappy-Bird-Game-Unity.git](https://github.com/svk-vasanthkumar/Flappy-Bird-Game-Unity.git)
    ```
2.  **Open in Unity:**
    Launch Unity Hub, click `Add Project`, and select the cloned directory. *(Note: Built with legacy Unity 5.6; upgrading to a modern LTS version may require an automatic API update by the engine).*
3.  **Load Scene:**
    Navigate to `Assets/Scenes/` and double-click the main scene.
4.  **Play:**
    Hit the **Play ▶️** button in the Unity Editor toolbar. Click the Game view to flap!

---

## 💼 Why This Project Matters (Portfolio Highlights)

This repository demonstrates fundamental game programming concepts highly relevant to Unity development:
* **Physics & Input:** Handling real-time `Rigidbody2D` manipulation via user input.
* **Memory Management:** Implementing a spawner and destroyer pattern to keep the hierarchy clean during infinite generation.
* **Component Communication:** Using modular scripts (like separating scoring from player movement) rather than monolithic code blocks.
* **Event Handling:** Utilizing Unity's `OnTriggerEnter2D` and `OnCollisionEnter2D` for seamless game state branching.

---

## 📸 Gameplay Gallery

<details>
<summary>Click to view screenshots</summary>

*(Replace these placeholders with actual paths to your repository images)*
* [Main Menu / Intro State](#)
* [Active Gameplay](#)
* [Game Over Screen](#)

</details>

---

## 📚 Asset Credits

* **Visuals:** Original Flappy Bird sprite style resources. 
* **Audio:** Sound effect resources credited to their respective original creators as noted in previous documentation.

---

## 🛣️ Future Ideas

* Add difficulty scaling (pipes spawn closer together over time).
* Implement persistent High Score saving using `PlayerPrefs`.
* Create a Day/Night cycle based on elapsed time.
* Compile a dedicated touch-friendly mobile build (APK).

---

## 📄 License

License information is not currently specified in the repository.

---

<div align="center">

**👨‍💻 Built by [svk-vasanthkumar](https://github.com/svk-vasanthkumar)**

> 🐦 **Can you beat your high score?**
> 
> **[⭐ Star the repo](https://github.com/svk-vasanthkumar/Flappy-Bird-Game-Unity/stargazers)** | **[🍴 Fork it](https://github.com/svk-vasanthkumar/Flappy-Bird-Game-Unity/network/members)**

</div>
