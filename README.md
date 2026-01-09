# hyprland-setup
[![Hyprland](https://img.shields.io/badge/Hyprland-Latest-5e81ac?style=for-the-badge&logo=linux&logoColor=white)](https://hyprland.org)
[![Arch Linux](https://img.shields.io/badge/Arch_Linux-1793D1?style=for-the-badge&logo=arch-linux&logoColor=white)](https://archlinux.org/)

My personal Hyprland configurations (Arch Linux + Hyprland).

# What it contains
- Multi-layout keyboard configurations (ABNT2 + US International)
- Custom input device adjustments
- Troubleshooting and computer migration documentation

# Contributions
Suggestions and feedback are welcome!

---

# Switching Laptops
## [Input.conf][link-input] (~/.config/hypr/input.conf)

[link-input]: https://github.com/jesseburlamaque/my-hyprland/blob/main/input.conf


This file documents the configuration of multiple keyboards with different layouts in Hyprland, allowing simultaneous use of:

- Laptop keyboard: ABNT2 layout (Brazilian Portuguese with cedilla)
- External Logitech K380 keyboard: US International layout (with accents via AltGr)

## Step 1: Identify the Devices
Run in the terminal:

```
hyprctl devices
```

## Step 2: Locate the Internal Keyboard Name
Look in the Keyboards section for the laptop's integrated keyboard. Common examples:

- at-translated-set-2-keyboard (most common)
- atkbd-serio0
- May vary depending on the laptop manufacturer

## Step 3: Update the Configuration
In the ~/.config/hypr/input.conf file, replace only the laptop device name:

```
device {
  name = keyboard-k380-keyboard ##Nome do Teclado Aqui
  kb_layout = us
  kb_variant = altgr-intl
  kb_model = pc105
  kb_options =
}
```

## Step 4: Verify the Configuration
Reload Hyprland (Super + Escape) and run again:

```
hyprctl devices
```

Verify that the laptop keyboard shows:

```
active keymap: Portuguese (Brazil)
```

**Note:** The K380 maintains the same name (keyboard-k380-keyboard) on any computer.


# Animations

In /home/burlamaque/.config/hypr/looknfeel.conf add:

```
# Animations
animations {
    enabled = true
    bezier = mybezier, 0.05, 0.9, 0.1, 1.05
    animation = workspaces, 1, 6, mybezier, slidefade
}
```
