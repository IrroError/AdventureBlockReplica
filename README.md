# Block Adventure

A logic puzzle game developed for the Android platform using the Unity Game Engine. The gameplay combines the spatial management of Tetris with the sub-grid logic of Sudoku on a 9x9 grid. 

## 🎮 Gameplay Features
* **Core Mechanics:** Players drag and drop complex shapes onto the board to clear horizontal rows, vertical columns, and 3x3 sub-grids.
* **Snap Preview System:** A touch-optimized shadow system previews valid drop positions, solving the mobile "fat finger" problem by showing exactly where a shape will land.
* **Dynamic Progression:** Spawning shapes shift color palettes dynamically as score thresholds are reached, providing visual feedback of progression.
* **Combo & Bonus System:** Clearing multiple lines simultaneously or specific colored bonus blocks triggers distinct visual events and bonus points.
* **Resource Management:** A strategic "Request System" allows players to refresh unfavorable shapes, limited to three uses per game.

## ⚙️ Architecture & Technical Highlights
This project focuses on clean software engineering practices to address the specific challenges of grid-based mobile games, creating a highly modular and testable C# codebase.
* **Data-Driven Design (DDD):** Utilizes Unity's `ScriptableObject` architecture (Flyweight Pattern) to decouple game configuration—like shape matrix coordinates—from runtime logic, eliminating hard-coded magic numbers.
* **Event-Driven Communication:** Implements the Observer Pattern via C# Actions inside `GameEvents.cs` to ensure a decoupled system where the core grid logic runs completely independently of the UI components.
* **Algorithmic Optimization:** Uses pre-defined static array Lookup Tables to map grid indices for rows, columns, and sub-grids, drastically reducing grid evaluation checks from O(N^2) to a series of O(1) operations.
* **Custom Editor Tooling:** Features a custom Inspector override to render the board array as an intuitive visual grid of toggle buttons for rapid level design.
* **Data Persistence:** Implements robust binary serialization (`BinaryFormatter`) via a custom `BinaryDataStream` class for saving high scores securely, moving away from insecure `PlayerPrefs` implementations.

## 🛠️ Built With
* Unity Engine (2022 LTS)
* JetBrains Rider
* Target Platform: Android 10.0+

## 🚀 Future Roadmap
* Dedicated Audio Manager integration utilizing the existing Event Bus.
* An A-Star search algorithm-based Hint System to assist stuck players.
* Cloud save integration (e.g., Firebase) to replace local binary formatting for cross-device persistence.
