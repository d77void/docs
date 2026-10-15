# niri

**niri** is a scrollable-tiling Wayland compositor: windows are arranged in
columns on an endless strip that scrolls sideways, and workspaces are stacked
vertically.

| | |
|---|---|
| Login screen | greetd |
| Terminal | kitty |
| Bar | Waybar |
| Launchers | fuzzel, nwggrid, d77run |
| Notifications | dunst |
| Lock screen | swaylock, with Super + T or after 5 minutes idle; screen off after 10 |
| Browser | Brave |

## Where to change things

| What | File |
|---|---|
| keys, programs started with the session, keyboard, outputs, layout | `~/.config/niri/config.kdl` |
| the bar | `~/.config/waybar/` |
| fuzzel launcher and power menu | `~/.config/fuzzel/` |
| lock screen | `~/.config/swaylock/config` |

niri applies `config.kdl` as soon as it is saved. The originals are in
`/etc/skel/.config/`.

Programs started with the session are the `spawn-at-startup` lines in
`config.kdl`.

## Keys

**Super** is the modifier (`Mod`).

| Keys | Action |
|---|---|
| Super + Return | terminal |
| Super + D | fuzzel (application launcher) |
| Super + N | nwggrid (application grid) |
| Super + O | d77run |
| Super + B | web browser |
| Super + P | file manager (PCManFM) |
| Super + S | drop-down terminal |
| Super + T | lock screen |
| Super + X | power menu |
| Super + Q | close window |
| Super + Shift + O | overview of all windows |
| Super + 1 … 9 | go to workspace |
| Super + Ctrl + 1 … 9 | move column to workspace |
| Super + R | next preset column width |
| Super + F | maximize the column |
| Super + Shift + F | full screen |
| Super + C | center the column |
| Super + , / Super + . | take the next window into the column / put it out |
| Super + H/J/K/L or arrows | focus column left / window down / up / column right |
| Super + Ctrl + H/J/K/L or arrows | move column or window |
| Super + Shift + H/J/K/L or arrows | focus another monitor |
| Super + U / Super + I | workspace below / above |
| Super + Ctrl + U / Super + Ctrl + I | move column to the workspace below / above |
| Super + mouse wheel | change workspace |
| Super + Shift + 7 | list of shortcuts |

Volume and microphone keys work, also on the lock screen.

## Idle

After 5 minutes without input the screen locks (swaylock), after 10 it turns
off and comes back on with any input, and it always locks before the computer
suspends. This is `/usr/bin/screenlock`, started with the session.

On installations made from ISOs built before 16 October 2026 the screen
locks but never turns off. To fix it, install `wlopm`:

```sh
sudo xbps-install -S wlopm
```

and, in `/usr/bin/screenlock`, replace both `swaymsg "output * power off"`
and `swaymsg "output * power on"` with `wlopm --off '*'` and `wlopm --on '*'`.

## Keyboard layout

In `config.kdl`:

```text
input {
    keyboard {
        xkb {
            layout "pt"
        }
    }
}
```

## Wallpaper

The wallpaper is set at start-up by `sww`, which shows
`~/Wallpaper/background2.png` with `swww`. To use another image now:

```sh
swww img ~/Wallpaper/<image>
```
