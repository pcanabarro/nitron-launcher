# Nitron Server Launcher

A cross-platform desktop application for creating and managing game servers with an intuitive wizard-based interface.

## Download

**[Download Latest Release (Windows)](https://github.com/pcanabarro/nitron-launcher/releases/tag/v1.0.0)**

No Java installation required - just extract and run!

| Platform | Status |
|----------|--------|
| Windows 64-bit | [Download v1.0.0](https://github.com/pcanabarro/nitron-launcher/releases/download/v1.0.0/NitronServerLauncher-V1.0.0.zip) |
| macOS | Coming soon |
| Linux | Coming soon |

See [README.md](https://github.com/pcanabarro/nitron-launcher/blob/master/releases/README.md) for step-by-step.

## Supported Games

| Game | Versions              | Status |
|------|-----------------------|--------|
| **Minecraft** | 1.3.2 - 1.21.11       | Vanilla ✓, Mods (Fabric) ✓, Plugins (Paper/Spigot/Purpur) ✓ |
| **Counter-Strike 2** | Steam Version         | ✓ LAN Server (Listen Server) |
| **Unturned** | 3.23.13.0 - 3.23.15.0 | Planned |

### Minecraft Server Modes

| Mode | Loaders | Status |
|------|---------|--------|
| **Vanilla** | Official Mojang Server | ✓ Fully Working |
| **Mods** | Fabric ✓, Forge (Coming Soon), NeoForge (Coming Soon), Quilt (Coming Soon) | Partial |
| **Plugins** | Paper ✓, Spigot ✓, Purpur ✓ | ✓ Fully Working |

### Counter-Strike 2 Server

| Feature | Description | Status |
|---------|-------------|--------|
| **LAN Server** | Creates listen server for local network play | ✓ Working |
| **Auto-Detection** | Automatically finds CS2 Steam installation | ✓ Working |
| **Launch Scripts** | Generates platform-specific start scripts (.bat/.sh) | ✓ Working |
| **Connection Info** | Creates HOW_TO_CONNECT.txt with player instructions | ✓ Working |

## Features

- **Main Menu Dashboard**: Central hub to create new servers or manage existing ones.
- **Server Management**:
    - **List View**: See all your created servers in one place.
    - **Dashboard**: Run, configure, and open local folders for each server.
    - **Direct Launch**: Start your server directly from the launcher with a dedicated console window.
- **Wizard-Based Setup**: 5-step guided server creation process.
- **Advanced Configuration**:
    - **Properties Editor**: specialized UI to edit `server.properties` (Port, Difficulty, Game Mode, etc.).
    - **Memory Allocation**: Set max RAM (Heap Size) for your server, with system memory detection.
- **Automatic Server Download**: Downloads official server files from Mojang API.
- **EULA Management**: Built-in EULA acceptance dialog for Minecraft.
- **Progress Tracking**: Real-time download progress with status updates.
- **Multiple Server Modes**: Vanilla, Mods, Plugins, or combined configurations.
- **Flexible Networking**: Auto-generated or dedicated IP configuration with custom port support.
- **Version Management**: Select from available game versions per game.
- **Modern UI**: Clean, dark-themed JavaFX interface.

## Technology Stack

- **Java 25** - Latest JDK features
- **JavaFX 25** - Modern UI framework
- **Maven** - Build and dependency management

## User Flow

### Main Menu
Start here. Choose to **Select Server** to manage an existing one, or **Create New Server** to start the wizard.

### Create New Server (Wizard)
1.  **Select Game**: Choose from Minecraft, Counter-Strike 2, or Unturned.
2.  **Select Version**: Pick a game version.
3.  **Select Mode**: Vanilla, Mods, Plugins, or Plugins & Mods.
4.  **Select Mod Loader** (conditional): Choose Fabric/Forge and version (shown only for MODS mode).
5.  **Select Plugin Loader** (conditional): Choose Paper/Spigot/Purpur and version (shown only for PLUGINS mode).
6.  **Configure Network**: IP and Port settings.
7.  **Review & Create**:
    *   Name your server.
    *   **Configure Properties**: Set advanced options like Difficulty, Game Mode, and **Max Memory** (RAM).
    *   **Run Server**: Launch immediately after creation.

### Manage Server
1.  **Server List**: View all created servers (highlighted selection).
2.  **Dashboard**:
    *   **Run Server**: Launch the server in a new console window.
    *   **Configure Properties**: Edit `server.properties` and memory allocation on the fly.
    *   **Open Folder**: Access raw files.

## License

This project is licensed under the MIT License - see the LICENSE file for details.

