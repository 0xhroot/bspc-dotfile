<div align="center">

```
██████╗ ███████╗██████╗  ██████╗    ██████╗  ██████╗ ████████╗███████╗
██╔══██╗██╔════╝██╔══██╗██╔════╝    ██╔══██╗██╔═══██╗╚══██╔══╝██╔════╝
██████╔╝███████╗██████╔╝██║         ██║  ██║██║   ██║   ██║   ███████╗
██╔══██╗╚════██║██╔═══╝ ██║         ██║  ██║██║   ██║   ██║   ╚════██║
██████╔╝███████║██║     ╚██████╗    ██████╔╝╚██████╔╝   ██║   ███████║
╚═════╝ ╚══════╝╚═╝      ╚═════╝    ╚═════╝  ╚═════╝   ╚═╝   ╚══════╝
```

**A full-stack bspwm rice — tiling WM, eww dashboard, Neovim, GTK theming & more**

[![bspwm](https://img.shields.io/badge/WM-bspwm-1E1E2E?style=for-the-badge&logo=linux&logoColor=white)](https://github.com/baskerville/bspwm)
[![sxhkd](https://img.shields.io/badge/Hotkeys-sxhkd-CBA6F7?style=for-the-badge)](https://github.com/baskerville/sxhkd)
[![Alacritty](https://img.shields.io/badge/Terminal-Alacritty-F38BA8?style=for-the-badge)](https://alacritty.org)
[![eww](https://img.shields.io/badge/Widget-eww-A6E3A1?style=for-the-badge)](https://github.com/elkowar/eww)
[![Neovim](https://img.shields.io/badge/Editor-Neovim-57A143?style=for-the-badge&logo=neovim&logoColor=white)](https://neovim.io)
[![Rofi](https://img.shields.io/badge/Launcher-Rofi-96CDFB?style=for-the-badge)](https://github.com/davatorium/rofi)
[![Zsh](https://img.shields.io/badge/Shell-Zsh-FAB387?style=for-the-badge)](https://www.zsh.org)
[![Shell](https://img.shields.io/badge/Shell-48.9%25-89DCEB?style=for-the-badge&logo=gnubash&logoColor=black)](.)
[![Lua](https://img.shields.io/badge/Lua-21.7%25-2C2D72?style=for-the-badge&logo=lua&logoColor=white)](.)

<br/>

> *"Not just a window manager. A complete environment."*

<br/>

[**Stack**](#-full-stack) · [**Structure**](#-file-structure) · [**Install**](#-installation) · [**Keybinds**](#️-keybindings) · [**Screenshots**](#-screenshots)

</div>

---

## 🖥️ Overview

This is a **complete bspwm desktop environment** — not just a window manager config, but a fully cohesive system covering every layer of the desktop: window management, hotkeys, bar, widgets, terminal, editor, launcher, notifications, right-click menu, GTK theming, shell, and fetch. Everything is color-coordinated and works together out of the box.

Built on **bspwm** — the binary space partitioning window manager — where every window placement decision is driven by a clean tree-based algorithm. Paired with **sxhkd** for hotkeys and an **eww dashboard** for custom widgets built in SCSS.

### At a glance

| Layer | Tool |
|---|---|
| Window Manager | bspwm |
| Hotkey Daemon | sxhkd |
| Terminal | Alacritty |
| Shell | Zsh (`.zshrc` included) |
| Editor | Neovim (Lua config) |
| Widget System | eww (SCSS dashboard) |
| App Launcher | Rofi |
| Notifications | Dunst |
| Right-click Menu | jgmenu |
| Audio Visualizer | Cava |
| GTK Theme | gtk-2.0 + gtk-3.0 |
| Fetch | Neofetch (custom) |
| Scripting | Shell + PowerShell |

---

## 🧩 Full Stack

### 🪟 bspwm — Window Manager

bspwm represents all windows as leaves of a full binary tree. Unlike i3's manual tiling, bspwm is purely controlled via `bspc` commands — there is no built-in keybinding system, which is why sxhkd exists as a separate daemon.

Key characteristics of this config:
- Binary space partitioning — windows split the available space automatically
- External rule system — window rules written as clean `bspc rule` commands
- Gap configuration — inner/outer gaps for breathing room
- Multiple desktop (workspace) support
- Autostart — launches sxhkd, eww, and compositor on startup

### ⌨️ sxhkd — Hotkey Daemon

sxhkd (Simple X Hotkey Daemon) handles all keyboard shortcuts independently of bspwm. It reads an `sxhkdrc` file and executes shell commands on keypress. This separation means keybinds work even if the WM crashes.

### 🖥️ Alacritty — Terminal

GPU-accelerated terminal emulator written in Rust. This config includes:
- Custom color scheme matching the overall palette
- Font configuration with Nerd Font support
- Opacity / background blur settings
- Padding and scrollback tuning

### 🐚 Zsh — Shell
`.zshrc` at repo root

A full Zsh configuration included at the root level:
- Custom prompt (likely Starship or manual PS1)
- Aliases and functions
- Plugin configuration
- Consistent with the terminal color theme

### 📝 Neovim — Editor
`nvim/` — **21.7% of the repo is Lua**

A complete Neovim config written entirely in Lua — the modern standard for Neovim configuration. Includes:
- Plugin manager setup (likely lazy.nvim or packer)
- LSP configuration for code intelligence
- Syntax highlighting via Treesitter
- Custom colorscheme matching the desktop theme
- Statusline, file explorer, fuzzy finder

### 🪟 eww — Widget Dashboard
`eww/dashboard/` — **14.5% of the repo is SCSS**

Elkowar's Wacky Widgets — a fully custom widget system written in Yuck (markup) and styled with SCSS. This is the most technically sophisticated component in the setup:
- Custom dashboard panel (system stats, clock, widgets)
- SCSS styling for pixel-perfect design control
- Reactive widgets that update from shell scripts
- Styled to match the overall color theme

This is what separates a basic rice from a proper desktop environment.

### 🚀 Rofi — App Launcher
`rofi/`

Themed application launcher with:
- Custom `.rasi` stylesheet
- dmenu mode for scripts
- Window switcher integration with bspwm desktops
- Color scheme matching the full palette

### 🔔 Dunst — Notification Daemon
`dunst/`

Lightweight notification daemon replacing the default system notifications:
- Custom `dunstrc` with themed colors
- Position, timeout, and size configuration
- Icon support
- Urgency-based color differentiation (low / normal / critical)

### 📋 jgmenu — Right-click Desktop Menu
`jgmenu/`

A right-click context menu for the desktop — uncommon in modern rices, making this setup more complete:
- Custom theme matching the desktop palette
- Configured menu items and categories
- Clean minimal styling

### 🎨 GTK Theming — gtk-2.0 & gtk-3.0
`gtk-2.0/` and `gtk-3.0/`

Full GTK application theming — meaning GUI apps like file managers, browsers, and dialogs match the desktop aesthetic:
- `gtk-2.0/` — legacy GTK2 app support
- `gtk-3.0/` — modern GTK3 app theming
- Consistent colors with the rest of the rice
- Custom cursor and icon theme references

### 🎵 Cava — Audio Visualizer
`cava/`

Terminal-based audio spectrum visualizer configured to match the color theme. Can run in a dedicated Alacritty window as a visual accent.

### 📟 Neofetch — System Fetch
`neofetch/`

Custom neofetch configuration with:
- Custom ASCII art or image display
- Selected info fields
- Color output matching the palette

### 💻 PowerShell
`powershell/` — **13.8% of the repo**

PowerShell scripts included for cross-platform utility or Windows-side dotfile management — rare in a Linux rice and shows a multi-platform workflow.

---

## 📁 File Structure

```
bspc-dotfile/
│
├── alacritty/                 # Alacritty terminal config
│   └── alacritty.toml         # Colors, font, opacity, padding
│
├── cava/                      # Cava audio visualizer
│   └── config                 # Colors, bars, sensitivity
│
├── dunst/                     # Dunst notification daemon
│   └── dunstrc                # Notification style & behavior
│
├── eww/
│   └── dashboard/             # eww widget dashboard (SCSS)
│       ├── eww.yuck            # Widget definitions & layout
│       ├── eww.scss            # Dashboard styles
│       └── scripts/           # Shell scripts feeding widget data
│
├── gtk-2.0/                   # GTK2 application theming
│   └── gtkrc
│
├── gtk-3.0/                   # GTK3 application theming
│   ├── gtk.css
│   └── settings.ini
│
├── jgmenu/                    # Right-click desktop menu
│   ├── jgmenurc               # Menu behavior config
│   └── theme/                 # Visual theme files
│
├── neofetch/                  # Neofetch system info
│   └── config.conf            # Fields, layout, ASCII art
│
├── nvim/                      # Neovim editor (full Lua config)
│   ├── init.lua               # Entry point
│   ├── lua/
│   │   ├── plugins/           # Plugin declarations
│   │   ├── config/            # Plugin configurations
│   │   └── core/              # Options, keymaps, autocmds
│   └── lazy-lock.json         # Plugin lock file
│
├── powershell/                # PowerShell scripts
│   └── *.ps1
│
├── rofi/                      # Rofi launcher theme
│   └── *.rasi
│
└── .zshrc                     # Zsh shell configuration
```

---

## 🎨 Color Palette

A dark, cohesive palette consistent across every component — terminal, editor, widgets, GTK apps, and notifications.

```
  Base        #1E1E2E  ████  Deep midnight blue
  Mantle      #181825  ████  Darker background
  Surface     #313244  ████  Surface / selection
  Text        #CDD6F4  ████  Primary text
  Subtext     #A6ADC8  ████  Dimmed text
  Lavender    #B4BEFE  ████  Accent blue
  Mauve       #CBA6F7  ████  Purple accent
  Pink        #F38BA8  ████  Pink / red highlight
  Green       #A6E3A1  ████  Success / active
  Peach       #FAB387  ████  Warning / orange
  Sky         #89DCEB  ████  Info / teal
```

> This palette is consistent with **Catppuccin Mocha** — check your actual config files to verify the exact hex values used.

---

## ⚙️ Installation

### Prerequisites

| Requirement | Notes |
|---|---|
| Arch Linux / BlackArch | Or any Arch-based distro |
| Xorg | bspwm requires X11 |
| AUR helper | `yay` or `paru` recommended |
| Nerd Fonts | For icons in bar, terminal, nvim |

### Step 1 — Clone

```bash
git clone https://github.com/0xhroot/bspc-dotfile.git
cd bspc-dotfile
```

### Step 2 — Install core dependencies

```bash
sudo pacman -S bspwm sxhkd alacritty rofi dunst picom feh zsh neovim \
               cava neofetch jgmenu

# AUR packages
yay -S eww-git
```

### Step 3 — Copy configs

```bash
# Create config directories
mkdir -p ~/.config/{bspwm,sxhkd,alacritty,rofi,dunst,eww,nvim,cava,jgmenu,neofetch}

# Copy each component
cp -r alacritty/*   ~/.config/alacritty/
cp -r cava/*        ~/.config/cava/
cp -r dunst/*       ~/.config/dunst/
cp -r eww/*         ~/.config/eww/
cp -r gtk-2.0/*     ~/.config/gtk-2.0/
cp -r gtk-3.0/*     ~/.config/gtk-3.0/
cp -r jgmenu/*      ~/.config/jgmenu/
cp -r neofetch/*    ~/.config/neofetch/
cp -r nvim/*        ~/.config/nvim/
cp -r rofi/*        ~/.config/rofi/
cp    .zshrc        ~/.zshrc

# Make bspwm scripts executable
chmod +x ~/.config/bspwm/bspwmrc
chmod +x ~/.config/sxhkd/sxhkdrc
```

### Step 4 — Set Zsh as default shell

```bash
chsh -s $(which zsh)
```

### Step 5 — Install Neovim plugins

```bash
nvim  # Open Neovim — plugins will auto-install on first launch
```

### Step 6 — Restart or login to bspwm

If already in a session:
```bash
bspc wm -r
```

Or log out and select bspwm from your display manager.

---

## ⌨️ Keybindings

> `super` = Win key. All binds are defined in `sxhkd/sxhkdrc`.

### Window Management

| Keybind | Action |
|---|---|
| `super + Return` | Open terminal (Alacritty) |
| `super + d` | Open Rofi launcher |
| `super + q` | Close focused window |
| `super + f` | Toggle fullscreen |
| `super + space` | Toggle floating |
| `super + t` | Set tiling mode |

### Focus & Move

| Keybind | Action |
|---|---|
| `super + h/j/k/l` | Focus window (left/down/up/right) |
| `super + shift + h/j/k/l` | Move window in direction |
| `super + alt + h/j/k/l` | Resize window |

### Desktops (Workspaces)

| Keybind | Action |
|---|---|
| `super + 1–9` | Switch to desktop |
| `super + shift + 1–9` | Send window to desktop |
| `super + Tab` | Last desktop |

### System

| Keybind | Action |
|---|---|
| `super + shift + r` | Reload sxhkd config |
| `super + shift + q` | Quit bspwm |
| `super + e` | Open eww dashboard |

> Edit `sxhkd/sxhkdrc` to see and customize all binds.

---

## 🆚 bspwm vs i3 — Why the switch?

This repo is a natural evolution from the [i3-dotfile](https://github.com/0xhroot/i3-dotfile). Here's what changed:

| Feature | i3wm | bspwm |
|---|---|---|
| Layout algorithm | Manual tiling | Binary space partitioning |
| Keybind system | Built-in | External (sxhkd) — more flexible |
| Scriptability | Limited | Full — every action is a `bspc` CLI call |
| Widget system | Polybar only | eww — full custom SCSS widgets |
| Config language | DSL | Shell scripts + sxhkdrc |
| Learning curve | Lower | Higher — more powerful |
| GTK theming | ❌ not in i3 rice | ✅ full gtk-2.0 + gtk-3.0 |
| Notifications | ❌ not in i3 rice | ✅ Dunst |
| Editor config | ❌ not included | ✅ Full Neovim Lua config |

---

## 📦 Dependencies Reference

| Package | Source | Purpose |
|---|---|---|
| `bspwm` | pacman | Window manager |
| `sxhkd` | pacman | Hotkey daemon |
| `alacritty` | pacman | Terminal emulator |
| `rofi` | pacman | App launcher |
| `dunst` | pacman | Notification daemon |
| `picom` | pacman | Compositor |
| `feh` | pacman | Wallpaper setter |
| `zsh` | pacman | Shell |
| `neovim` | pacman | Editor |
| `cava` | pacman | Audio visualizer |
| `neofetch` | pacman | System fetch |
| `jgmenu` | pacman | Right-click desktop menu |
| `eww-git` | AUR | Widget dashboard engine |
| Nerd Fonts | AUR | Icon glyphs |

---

## 🗺️ Roadmap

- [ ] Add bspwmrc and sxhkdrc to repo (core WM configs)
- [ ] Add picom compositor config
- [ ] Add wallpaper assets
- [ ] Add lockscreen config (betterlockscreen)
- [ ] Add screenshot tool (maim / flameshot keybind)
- [ ] Document all eww dashboard widgets
- [ ] Add Starship prompt config
- [ ] Multi-monitor setup guide

---

## 📄 License

```
MIT License — Copyright (c) 2025 0xhroot

Use it. Fork it. Rice it. A star is appreciated. ⭐
```

---

<div align="center">

**Crafted by [0xhroot](https://github.com/0xhroot)**

*bspwm. eww. Neovim. The full stack desktop.*

[![GitHub](https://img.shields.io/badge/GitHub-0xhroot-181717?style=for-the-badge&logo=github)](https://github.com/0xhroot)
[![i3 Rice](https://img.shields.io/badge/Also%20See-i3--dotfile-6C7086?style=for-the-badge&logo=linux&logoColor=white)](https://github.com/0xhroot/i3-dotfile)

</div>
