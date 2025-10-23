# Pebble Downloads

This directory contains the release binaries and VS Code extension for Pebble.

## Building Releases

### On Linux
Run the build script:
```bash
./build_release.sh
```

This will create:
- `pebble-linux-v0.1.0.zip` - Linux binary
- `pebble-vscode-v0.1.0.vsix` - VS Code extension

### On macOS
Run the same build script:
```bash
./build_release.sh
```

This will create:
- `pebble-macos-v0.1.0.zip` - macOS binary
- `pebble-vscode-v0.1.0.vsix` - VS Code extension

### On Windows
Run the Windows batch script:
```cmd
build_release.bat
```

This will create:
- `pebble-windows-v0.1.0.zip` - Windows binary
- `pebble-vscode-v0.1.0.vsix` - VS Code extension

**Note**: Cross-compilation is not yet supported by Odin for linking. Each platform must be built on its native OS.

---

## Quick Start

### Linux/macOS
1. Download `pebble-linux-v0.1.0.zip` or `pebble-macos-v0.1.0.zip`
2. Extract: `unzip pebble-linux-v0.1.0.zip`
3. Make executable: `chmod +x pebble-linux`
4. Run: `./pebble-linux yourscript.pbl`

### Windows
1. Download `pebble-windows-v0.1.0.zip`
2. Extract the zip file
3. Run: `pebble-windows.exe yourscript.pbl`

## VS Code Extension

Install the `.vsix` file in VS Code:

**Method 1 (UI):**
1. Open VS Code
2. Go to Extensions (Ctrl+Shift+X)
3. Click "..." menu → "Install from VSIX..."
4. Select `pebble-vscode-v0.1.0.vsix`

**Method 2 (CLI):**
```bash
code --install-extension pebble-vscode-v0.1.0.vsix
```

## System Requirements

- **OS**: Linux (x86_64), macOS (x86_64), or Windows (x86_64)
- **RAM**: 128 MB minimum
- **Disk**: 10 MB

## Documentation

Visit [pebble-lang.dev](https://pebble-lang.dev) for:
- Language documentation
- Syntax cheatsheet
- Examples and tutorials
- Architecture details
