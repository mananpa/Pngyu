# Pngyu

Pngyu is a GUI image compression application. It uses [pngquant](https://pngquant.org/) for PNG files and Qt's built-in image engine for all other supported formats.

## Supported Formats

| Format | Extension(s) | Compression engine |
|--------|--------------|--------------------|
| PNG | `.png` | pngquant (palette quantization) |
| Animated PNG | `.apng` | pngquant |
| JPEG | `.jpg` `.jpeg` | Qt JPEG encoder |
| WebP | `.webp` | Qt WebP encoder |
| AVIF | `.avif` | Qt AVIF plugin (if available) |
| TIFF | `.tiff` `.tif` | Qt TIFF encoder (LZW) |
| HEIC | `.heic` | Qt HEIC plugin (if available) |
| BMP | `.bmp` | Qt BMP encoder |

> **Note:** HEIC and AVIF require the corresponding Qt image plugins to be installed on the system. All other formats work out of the box.

### Compression quality for non-PNG formats

When using **Custom** compress mode, the *Colors* slider (2–256) maps to an image quality value (1–95). A higher color count produces a higher-quality, larger output; a lower color count produces a smaller, lower-quality output. In **Default** mode, Qt applies each format's own default quality.

pngquant is only required when PNG or APNG files are in the file list. The app works without pngquant for all other formats.

## Download

Download the latest version from the [Homepage](https://nukesaq88.github.io/Pngyu/).

Pre-built binaries are available for Windows and macOS.

## Building from Source

Pngyu can be built on any platform that supports Qt and pngquant command-line tool.

### Requirements
- Qt 6.x
- CMake 3.16 or later
- C++17 compatible compiler
- pngquant binary (included in `pngquant_bin` directory)

### Build Instructions

#### Command Line

**macOS:**
```bash
./scripts/build_mac.sh
```

The built application will be available at `build/Release/Pngyu.app`.

To build Debug version:
```bash
BUILD_TYPE=Debug ./scripts/build_mac.sh
```

**Windows:**
```powershell
.\scripts\build_win.ps1
```

To build Debug version:
```powershell
.\scripts\build_win.ps1 -BuildType Debug
```

#### Qt Creator

1. Open `CMakeLists.txt` in Qt Creator
2. In the "Configure Project" screen, set the build directory to `build/Release` (for Release builds) or `build/Debug` (for Debug builds)
3. Build the project (Ctrl+B / Cmd+B)

The built application will be in the configured build directory.

### Distribution

After building, use the deployment scripts to create distributable packages:

**macOS:**
```bash
./scripts/deploy_mac.sh
```

This will bundle Qt frameworks and create a DMG file.

**Windows:**
```powershell
.\scripts\deploy_win.ps1
```

This will bundle Qt DLLs and create an archive.

The deployment scripts work with both command-line and Qt Creator builds, as long as the build directory is `build/Release` (configurable via `BUILD_DIR` environment variable).

## Internationalization (i18n)

Pngyu supports multiple languages. For information about translations and contributing new languages, see [translations/README.md](translations/README.md).

## License

Pngyu itself is distributed under the BSD license.

However, the pre-built binaries include pngquant, which is licensed under GPL v3 or later.
See https://github.com/kornelski/pngquant for pngquant's license details.
