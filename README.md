# macOS-app-icon-builder

Generate a macOS app icon set (`icons.iconset/`) from a single PNG (recommended: 1024×1024), and package it into an `.icns` file.

## Requirements (macOS only)

- **macOS is required**
- Uses built-in macOS tools:
  - `sips` (image resizing)
  - `iconutil` (converts `icons.iconset/` to `.icns`)

Because `sips` and `iconutil` are macOS-only, this project will not work on Linux or Windows.

## Quick Start

From the repo root:

```bash
chmod +x build-icon
```

### 1) Generate the default output (`icon.icns`)

```bash
./build-icon your-logo.png
```

Outputs:
- `icons.iconset/` (intermediate output; recreated every run)
- `icon.icns` (default final output)

### 2) Choose the output filename

```bash
./build-icon your-logo.png MyApp.icns
```

## Usage

```bash
./build-icon <input.png> [output.icns]
```

Arguments:
- `<input.png>`: input PNG path (relative or absolute)
- `[output.icns]`: optional output `.icns` path (default: `icon.icns`)

Help:

```bash
./build-icon --help
```

## Notes

- The script deletes and recreates `icons.iconset/` on every run to keep results consistent.
- Generated sizes include: 16, 32, 64, 128, 256, 512, 1024 (plus the corresponding @2x variants).

## FAQ

### Why does this require macOS?

This tool relies on `sips` and `iconutil`, which are built into macOS and are not available by default on Linux/Windows.

### What PNG size should I use?

Use a square **1024×1024** PNG (with comfortable padding) for best quality.

If you need a macOS-compliant 1024×1024 source PNG for building app icons, you can generate one using a tool like https://github.com/yc-w-cn/macos-compliant-icon-generator.
