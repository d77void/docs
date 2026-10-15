# Sway

**Sway** is a tiling Wayland compositor compatible with i3: windows are placed
side by side automatically and workspaces are numbered. d77void installs
**SwayFX**, a Sway with extra visual effects, and uses Sway's own bar.

| | |
|---|---|
| Login screen | greetd |
| Terminal | kitty |
| Bar | Sway's bar (`swaybar`), filled by `~/.config/sway/status.sh` |
| Launchers | wmenu, fuzzel, nwggrid, d77run |
| Notifications | SwayNotificationCenter |
| Lock screen | swaylock, after 5 minutes idle (screen off after 10) |

## Where to change things

| What | File |
|---|---|
| keys, programs started with the session, keyboard, gaps, wallpaper, idle | `~/.config/sway/config` |
| what the bar shows | `~/.config/sway/status.sh` |
| colour themes (Catppuccin) | `~/.config/sway/catppuccin-*` |
| notifications | `~/.config/swaync/` |
| lock screen | `~/.config/swaylock/config` |
| fuzzel launcher and power menu | `~/.config/fuzzel/` |

After saving `config`, press **Super + Shift + C** to reload it. The originals
are in `/etc/skel/.config/`.

## Keys

**Super** is the modifier (`$mod`).

| Keys | Action |
|---|---|
| Super + Return | terminal |
| Super + D | wmenu |
| Super + P | fuzzel (application launcher) |
| Super + N | nwggrid (application grid) |
| Super + O | d77run |
| Super + X | power menu |
| Super + T | lock screen |
| Super + Y | random wallpaper from `~/Wallpaper/` |
| Super + G, or Print | screenshot of the whole screen (`grim`; a PNG named after the date and time) |
| Super + Shift + Q | close window |
| Super + H/J/K/L or arrows | focus left / down / up / right |
| Super + Shift + H/J/K/L or arrows | move window |
| Super + 1 … 0 | go to workspace 1 … 10 |
| Super + Shift + 1 … 0 | move window to workspace |
| Super + B / Super + V | split horizontally / vertically |
| Super + S / W / E | layout: stacking / tabbed / toggle split |
| Super + F | full screen |
| Super + Shift + Space | float or tile the window |
| Super + Space | switch focus between floating and tiled |
| Super + Shift + − / Super + − | send to / show the scratchpad |
| Super + R | resize mode (arrows or H/J/K/L; Return or Escape to leave) |
| Super + Shift + C | reload the configuration |
| Super + Shift + E | exit Sway |

Volume, microphone and brightness keys work, also on the lock screen.

## Keyboard layout

In `~/.config/sway/config`:

```text
input type:keyboard {
    xkb_layout "pt"
    xkb_variant ""
}
```

## Wallpaper

The line `output * bg ~/Wallpaper/background3.png fill` in `config` sets the
wallpaper at start-up; change the file name to use another image. **Super +
Y** picks a random one from `~/Wallpaper/` for the current session.
