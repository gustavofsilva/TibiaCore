# TibiaCore Documentation

Welcome to the TibiaCore documentation. This project is a high-performance Open Tibia Server (OTS) emulator based on The Forgotten Server (TFS).

## Table of Contents
1. [Introduction](#introduction)
2. [Getting Started](#getting-started)
3. [Configuration (config.lua)](#configuration)
4. [Database Setup](#database-setup)
5. [Directory Structure](#directory-structure)

---

## Introduction
TibiaCore is designed to provide a stable and customizable environment for hosting Tibia servers. It features an optimized C++ engine and a flexible Lua scripting system for game logic.

**Key Features:**
*   **Anti-Rollback System**: Automatic server saving on crashes.
*   **Integrated Live Casting**: Allow players to broadcast their gameplay.
*   **Account Bonus System**: Experience and death penalty bonuses based on account type (Copper, Silver, Gold).
*   **Advanced Networking**: Built-in DDoS protection rules and optimized packet handling.

---

## Getting Started

### Ubuntu 22.04 Setup
1.  **Install Dependencies:**
    ```bash
    sudo apt update && sudo apt upgrade -y
    sudo apt install git cmake build-essential libluajit-5.1-dev libmariadb-dev-compat libboost-date-time-dev libboost-filesystem-dev libboost-system-dev libboost-iostreams-dev libpugixml-dev libgmp3-dev libcrypto++-dev libfmt-dev libjsoncpp-dev
    ```
2.  **Compile:**
    ```bash
    cd compiler
    mkdir build && cd build
    cmake ..
    make
    ```
3.  **Run:**
    ```bash
    cd ../..
    ./restart.sh
    ```

### Windows Setup
*   Use **Visual Studio 2017** or higher.
*   Install dependencies via `vcpkg` (see `README.md` for specific commands).
*   Open `compiler/vc17/theforgottenserver.vcxproj` and compile.

---

## Scripting System
TibiaCore uses a hybrid system for game logic:
*   **XML**: Used for registering entities (monsters, spells, vocations, items) and defining their basic properties.
*   **Lua**: Used for complex logic, such as quest triggers, custom spells, and NPC interactions. Scripts are located in `data/` and usually registered in a corresponding `.xml` file.

---

## Configuration (config.lua)
The `config.lua` file is the heart of your server's settings.

| Parameter | Description |
| :--- | :--- |
| `worldType` | Type of world: `pvp`, `no-pvp`, or `pvp-enforced`. |
| `ip` | The public IP address of your server. |
| `mysqlHost` | Database host (usually `127.0.0.1`). |
| `rateExp` | Experience rate multiplier. |
| `rateLoot` | Loot drop rate multiplier. |
| `whiteSkullTime` | Duration of the white skull in seconds. |

---

## Compiling from Source

### Ubuntu 22.04
1.  **Dependencies**: `sudo apt install git cmake build-essential libluajit-5.1-dev libmariadb-dev-compat libboost-date-time-dev libboost-filesystem-dev libboost-system-dev libboost-iostreams-dev libpugixml-dev libgmp3-dev libcrypto++-dev libfmt-dev libjsoncpp-dev`
2.  **Steps**:
    ```bash
    mkdir compiler/build && cd compiler/build
    cmake ..
    make -j$(nproc)
    ```

### Windows (Visual Studio 2017+)
1.  **VCPKG**: Use vcpkg to install `boost`, `luajit`, `mariadb`, `pugixml`, `cryptopp`, `fmt`, `mpir`.
2.  **Project**: Open `compiler/vc17/theforgottenserver.vcxproj`.
3.  **Build**: Set configuration to `Release` and architecture to `x64`, then build the solution.

---

## Database Setup
TibiaCore uses MySQL/MariaDB.

1.  **Create Database**: Create a database named `tibiacore` (or as configured in `config.lua`).
2.  **Import Schema**: Import the `tibiacore-empty.sql` file provided in the root directory.
3.  **Docker (Optional)**: If using Docker, `dbinstall.sh` handles the automated setup and import.

---

## Directory Structure
*   `compiler/`: C++ source code and build files.
*   `data/`: Game data (XMLs, Lua scripts, Map).
    *   `data/monster/`: Monster definitions.
    *   `data/talkactions/`: Custom player/staff commands.
    *   `data/npc/`: NPC definitions and scripts.
    *   `data/world/`: Map files (`.otbm`).
*   `logs/`: Server activity and error logs.
