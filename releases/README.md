# Nitron Server Launcher - Downloads

## Quick Start

### Step 1: Download
Download the latest version for your platform:
- **Windows**: `NitronServerLauncher-1.0.0-windows.zip`

### Step 2: Extract
1. Right-click the downloaded `.zip` file
2. Select "Extract All..."
3. Choose a location (e.g., `C:\Downloads\NitronServerLauncher`)
4. Click "Extract"

### Step 3: Run
1. Open the extracted folder
2. Double-click `NitronServerLauncher.exe`
3. No Java installation required - everything is bundled!

### Step 4: Create Your First Server
1. Click **"Create New Server"** on the main menu
2. Select your game (Minecraft or CS2)
3. Follow the wizard steps
4. Click **"Create Server"** and optionally **"Run Server"**

Your servers are saved in `~/game-servers/` (e.g., `C:\Users\YourName\game-servers\`)

---

## Available Downloads

| Platform | File | Size | Status |
|----------|------|------|--------|
| Windows 64-bit | `NitronServerLauncher-1.0.0-windows.zip` | ~150 MB | Available |
| macOS | Coming soon | - | Planned |
| Linux | Coming soon | - | Planned |

---

## Troubleshooting

### "Windows protected your PC" message
1. Click "More info"
2. Click "Run anyway"
3. This happens because the app isn't signed with a certificate yet

### Application won't start
- Make sure you extracted the entire folder, not just the .exe
- The `lib/` folder must be in the same directory as the .exe

### Server creation fails
- Check your internet connection (files are downloaded from official sources)
- For CS2: Make sure Steam is installed with CS2

---

## Verify Download (Optional)

```
SHA-256 (NitronServerLauncher-1.0.0-windows.zip):
<checksum will be added>
```

To verify on Windows PowerShell:
```powershell
Get-FileHash NitronServerLauncher-1.0.0-windows.zip -Algorithm SHA256
```
