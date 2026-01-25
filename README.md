# ghost_terminal

Translucent black terminal setup for GNOME with custom window tiling.

## The Look

- **Background:** Pure black `rgb(0,0,0)` with 42% transparency
- **Text:** Light green `rgb(150,213,162)`
- **Window size:** 96 columns x 42 rows

## Installation

### Terminal Profile

Import the GNOME Terminal profile:

```bash
dconf load /org/gnome/terminal/legacy/profiles:/ < profiles/gnome-terminal.dconf
```

### Window Tiling

1. Install dependencies:
```bash
sudo apt install wmctrl xdotool
```

2. Run the install script to set up Super+T keybinding:
```bash
./scripts/install_tiling_extension.sh
```

Or manually copy the tiler script:
```bash
cp scripts/wayland_window_tiler.py ~/.local/bin/gnome-window-tiler
chmod +x ~/.local/bin/gnome-window-tiler
```

## Tiling States

Press `Super+T` to cycle through:

1. Full screen (maximized)
2. Left half
3. Right half
4. Top-left quarter
5. Top-right quarter
6. Bottom-left quarter
7. Bottom-right quarter

## Files

```
ghost_terminal/
├── profiles/
│   └── gnome-terminal.dconf    # Terminal color/transparency settings
└── scripts/
    ├── wayland_window_tiler.py # Wayland-native tiling (gdbus)
    ├── window_tiler.py         # X11 tiling (wmctrl/xdotool)
    ├── install_tiling_extension.sh  # Super+T keybinding setup
    └── setup_native_tiling.sh  # Enable GNOME native tiling
```

## Native GNOME Shortcuts

These work out of the box after running `setup_native_tiling.sh`:

| Shortcut | Action |
|----------|--------|
| Super+Left | Tile left half |
| Super+Right | Tile right half |
| Super+Up | Maximize |
| Super+Down | Restore |
