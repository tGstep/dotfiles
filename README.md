# Dotfiles
A chill Hyprland configuration focused on comfort and productivity. This setup provides smooth animations, soft aesthetics, and practical keybindings for daily software dev laptop use.

## Overview

This configuration includes settings for:
- **Hyprland**: Wayland compositor with custom animations
- **Waybar**: Status bar with system information
- **Hyprpaper**: Wallpaper manager

I also use Ghostty as terminal and Rofi as application launcher in my daily workflow, but their configs aren't included here.

## Design Features

### Visual Style
The configuration focuses on visual comfort:
- Thin borders (1px) with soft pastel colors
- Subtle blur and shadow effects
- Smooth animations using comfortable bezier curves
- Reduced opacity for inactive windows

### Animation System
Custom curves provide natural motion:
- **easeOut**: Smooth deceleration for borders and fades
- **softOut**: Gentle endings for windows and layers
- **comfortable**: Balanced curve for global animations
- Slower timing (4-8ds) for relaxed transitions

### Keybindings
All primary bindings use `Super` as main modifier:
- `Super + T/B/Space/C`: Launch terminal, browser, menu, editor
- `Super + Q/F/Escape`: Close window, fullscreen, exit
- `Super + J`: Toggle horizontal/vertical split
- `Super + 1-0`: Switch to workspace
- `Super + Shift + 1-0`: Move window to workspace
- `Super + Arrows`: Navigate focus
- `Alt + Arrows`: Resize window
- Function keys: Volume, brightness, media controls

### Status Bar
Waybar shows essential information:
- 5 persistent workspaces
- Current window title (max 50 characters)
- System tray, Bluetooth, audio controls
- Battery with warnings at 30% and 15%
- Backlight percentage
- Clock (HH:MM) with date tooltip

## Dependencies

```bash
# Core components
sudo pacman -S hyprland waybar hyprpaper

# System utilities
sudo pacman -S brightnessctl playerctl wireplumber blueman pavucontrol

# Clipboard and screenshots
sudo pacman -S wl-clipboard cliphist grim slurp

# Fonts
sudo pacman -S ttf-jetbrains-mono-nerd
```

For `pass-secret-service`, check AUR.

## Installation

```bash
# Clone repository
git clone <repository-url> ~/dotfiles
cd ~/dotfiles

# Backup existing configs
mkdir -p ~/.config/backup
mv ~/.config/hypr ~/.config/backup/ 2>/dev/null
mv ~/.config/waybar ~/.config/backup/ 2>/dev/null

# Create symbolic links
ln -sf ~/dotfiles/hypr ~/.config/
ln -sf ~/dotfiles/waybar ~/.config/
```

Lastly exit Hyprland with `Super + Escape` and re-open it running `start-hyprland`.

## Configuration Files

### hyprland.conf
Main compositor settings including window management, keybindings, animations, and visual styling.

### hyprpaper.conf
Wallpaper settings for monitor `eDP-1`. Update the `path` to change wallpaper.

### waybar/config.jsonc
Module layout and settings. Customize visible modules and workspace count here.

### waybar/style.css
Visual styling for the status bar. Change colors, padding, and effects here.

## Customization

### Animation Speed
Change animation timing in `hyprland.conf`. Higher values slow down animations, lower values speed them up.

### Colors
Modify borders in the `general` section:
```bash
col.active_border = rgba(88ccffaa) rgba(99eeddaa) 45deg
col.inactive_border = rgba(44444466)
```

Update Waybar colors in `style.css`.

### Waybar Modules
Edit `modules-left`, `modules-center`, and `modules-right` arrays in `config.jsonc`.

### Workspace Count
Change persistent workspace count:
```json
"persistent-workspaces": { "*": 5 }
```

## Features

- Dwindle tiling layout for balanced window management
- Optimized blur (size 5, passes 2) for smooth performance
- Print key screenshots with grim and slurp
- Three-finger swipe for workspace switching on touchpad
- 80% opacity for inactive windows
- Bind caps lock key to escape for nvim comfort

## Technical Details

- Cursor size: 24px
- Keyboard layout: Italian
- Wayland backend enabled for Firefox
- Window resizing on borders and gaps
- Auto monitor detection

## License

MIT License
