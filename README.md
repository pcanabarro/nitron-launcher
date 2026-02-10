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

## Prerequisites

- Java Development Kit (JDK) 25 or higher
- Maven 3.6+

Verify installation:
```bash
java -version
mvn -version
```

## Installation

### Clone the Repository

```bash
git clone https://github.com/pcanabarro/launcher.git
cd launcher
```

### Build and Run

```bash
# Compile the project
mvn compile

# Run the application
mvn javafx:run

# Or clean build and run
mvn clean javafx:run
```

## Project Structure

```
launcher/
├── src/
│   ├── main/java/launcher/
│   │   ├── MainApp.java          # Application entry point
│   │   ├── models/               # Domain models & enums
│   │   ├── core/                 # Business logic layer
│   │   │   ├── creator/          # Server creation strategies
│   │   │   ├── runtime/          # Server runtime management
│   │   │   │   └── launch/       # Game-specific launch commands
│   │   │   ├── minecraft/        # Minecraft-specific logic
│   │   │   └── cs2/              # CS2-specific logic
│   │   └── ui/                   # JavaFX presentation layer
│   │       ├── components/       # Reusable UI components
│   │       └── dialog/           # Dialogs and property builders
│   └── test/java/launcher/       # Unit tests
├── pom.xml                       # Maven configuration
├── CLAUDE.md                     # Developer documentation
└── README.md
```

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

## Architecture

### Layer Structure

- **Models** (`launcher.models`) - Domain enums and state objects
- **Core** (`launcher.core`) - Business logic and services
  - `ServerManager.java` - Manages filesystem paths and lists existing servers.
  - `creator/` - Game-specific server creators (Strategy pattern)
  - `minecraft/` - Minecraft-specific implementation
- **UI** (`launcher.ui`) - JavaFX view classes.

### Design Patterns

- **Strategy Pattern**: `GameServerCreator` interface allows game-specific implementations
- **Factory Pattern**: `GameServerCreatorFactory` returns the appropriate creator per game
- **Facade Pattern**: `ServerCreator` provides a simple API, delegating to game-specific creators

### Key Components

| Component | Description |
|-----------|-------------|
| `MainApp` | Entry point, manages Stage and wizard navigation |
| `ServerManager` | Discovering and resolving paths for existing servers |
| `ServerConfig` | Abstract base class for server configuration |
| `MinecraftServerConfig` | Minecraft-specific config (gameMode, modLoader, pluginLoader) |
| `CS2ServerConfig` | CS2-specific config (defaultMap, maxPlayers, password, friendlyFire) |
| `ServerConfigFactory` | Factory to create game-specific ServerConfig instances |
| `LauncherService` | Provides available versions per game |
| `ServerCreator` | Facade for server creation, delegates to game-specific creators |
| `GameServerCreator` | Strategy interface for game-specific server creation |
| `MinecraftServerCreator` | Downloads server JAR from Mojang, configures Minecraft servers |
| `CS2ServerCreator` | Creates CS2 LAN servers with launch scripts and config |
| `MinecraftVersionManifest` | Fetches version metadata from Mojang's API (with caching) |
| `NetworkUtils` | Detects local IP addresses for server connection info |

## Development

### Adding New Games

1. Add enum value to `Game.java`
2. Add version mappings in `LauncherService.java` (`AVAILABLE_VERSIONS` map)
3. Implement game-specific logic in `ServerCreator.java`

### Configuration

| Setting | Location | Default |
|---------|----------|---------|
| Window Size | `MainApp.java` | 600x400 |
| Default Port | `ServerConfig.java` | 25565 |
| Available Versions | `LauncherService.java` | Per game |

### Styling

UI uses PlayStation DualSense eXplorer (DSX) inspired theme:
- **Backgrounds**: Very dark blue-black (`#0A0E1A`, `#12161F`, `#1A1F2E`)
- **Primary Accent**: Darker PlayStation blue (`#0050A0`)
- **Secondary Accent**: Lighter blue (`#4A9EFF`)
- **Text**: White (`#ffffff`), gray-blue (`#B8C5D6`), muted (`#6B7C93`)
- **Warning**: PlayStation orange (`#FF9500`)
- **Success**: PlayStation green (`#00C853`)

All theme constants centralized in `Theme.java`.

## Build Commands

```bash
# Compile
mvn compile

# Run
mvn javafx:run

# Package
mvn package

# Run tests
mvn test
```

## Troubleshooting

### JavaFX Module Errors

```bash
java --module-path /path/to/javafx-sdk/lib \
     --add-modules javafx.controls,javafx.fxml \
     -jar launcher.jar
```

### Build Issues

```bash
mvn dependency:purge-local-repository
mvn clean install
```

### Runtime Issues

- Verify Java 25 is installed: `java -version`
- Check JavaFX is in classpath
- Try software rendering: `-Dprism.order=sw`

## Roadmap

### Completed

- Minecraft Vanilla server creation (downloads from Mojang, EULA handling, server.properties)
- Minecraft Mods support: **Fabric** fully working (downloads loader, installs)
- Minecraft Plugins support: **Paper, Spigot, Purpur** fully working
- Dynamic mod/plugin loader version selection from official APIs
- Conditional wizard flow (shows loader selection only when needed)
- Progress tracking with real-time download status
- "Open Folder" quick access button
- Server Dashboard & List View
- Launching servers directly from UI
- Memory allocation configuration
- Reusable themed UI components (StyledButton, StyledComboBox)
- **Counter-Strike 2 LAN server creation** (auto-detects Steam installation, generates launch scripts)

### In Progress

- Additional Minecraft mod loaders: Forge, NeoForge, Quilt

### Planned Features

**Games & Content**
- Unturned server creation
- Additional games (Terraria, Valheim, ARK, Rust)
- Mod/plugin browser integration

**Server Management**
- Stop/restart controls (currently only Start)
- Console output viewer inside the app
- Server status indicators (CPU, RAM, player count)

**Configuration**
- Server presets/templates
- Import/export configurations
- Auto-update for game versions

**UX Improvements**
- Theme toggle (dark/light)
- Port conflict validation

**Infrastructure**
- Docker container support
- Remote server deployment
- Backup and restore
- Scheduled maintenance

## Contributing

Contributions are welcome! Please feel free to submit pull requests or open issues for bugs and feature requests.

## License

This project is licensed under the MIT License - see the LICENSE file for details.
