# mango

**MangoWC** (`mango`) is a Wayland compositor descended from dwl, with several
layouts (tiling, scrolling, dwindle and more), an overview of all windows,
animations and numbered *tags* as workspaces. It is configured with one text
file.

| | |
|---|---|
| Login screen | greetd |
| Terminal | kitty |
| Bar | Waybar |
| Launchers | fuzzel, nwggrid, d77run |
| Notifications | dunst |
| Lock screen | swaylock, with Super + T or after 5 minutes idle; screen off after 10 |

## Where to change things

| What | File |
|---|---|
| keys, programs started with the session, keyboard, layouts, look | `~/.config/mango/config.conf` |
| environment variables | `~/.config/mango/env.conf` |
| the bar | `~/.config/waybar/` |
| fuzzel launcher and power menu | `~/.config/fuzzel/` |

Programs started with the session are the `exec_once=` lines. Press
**Super + R** after saving to reload the configuration. The originals are in
`/etc/skel/.config/mango/`.

## Keys

Most actions use **Alt**; workspace and session actions use **Super**.

| Keys | Action |
|---|---|
| Alt + Return | terminal |
| Alt + Space | fuzzel (application launcher) |
| Alt + N | nwggrid (application grid) |
| Alt + R | d77run |
| Alt + Q | close window |
| Alt + Z | drop-down (scratchpad) |
| Alt + Tab | overview of all windows |
| Alt + F | full screen |
| Alt + A | maximize |
| Alt + \\ (backslash) | float or tile the window |
| Alt + arrows | focus the window in that direction |
| Super + Shift + arrows | swap with the window in that direction |
| Super + Tab | focus the next window |
| Super + N | next layout |
| Ctrl + 1 … 9 | go to tag |
| Alt + 1 … 9 | move window to tag |
| Super + Left / Right | previous / next tag |
| Alt + Shift + Left / Right | focus the monitor on the left / right |
| Super + left mouse button / right mouse button | move / resize a window |
| Super + R | reload the configuration |
| Super + T | lock screen |
| Super + X | power menu |
| Super + M | quit mango |

## Idle

After 5 minutes without input the screen locks, after 10 it turns off and
comes back on with any input, and it always locks before the computer
suspends. This is the `exec_once=swayidle …` line in `config.conf`.
Installations made from ISOs built before 16 October 2026 have no lock
screen; to add it, install `swaylock`, `swayidle` and `wlopm` and copy that
line and the `bind=SUPER,t,spawn,swaylock -f` line from
`/etc/skel/.config/mango/config.conf` of a newer ISO, or from this page:

```text
exec_once=swayidle -w timeout 300 'swaylock -f' timeout 600 "wlopm --off '*'" resume "wlopm --on '*'" before-sleep 'swaylock -f'
bind=SUPER,t,spawn,swaylock -f
```

## Keyboard layout

In `config.conf`:

```text
xkb_rules_layout=pt
```

## Wallpaper

The line `exec_once=swaybg -i Wallpaper/d77void_2560x1600.png -m fill` sets it
at start-up; change the file name to another image in `~/Wallpaper/`.
