# river

**river** is a dynamic tiling Wayland compositor. Its configuration is a
shell script, `init`, that runs `riverctl` commands; the layout (where windows
go) is drawn by a separate program, `rivertile`. Workspaces are *tags*, as in
dwm.

| | |
|---|---|
| Login screen | greetd |
| Terminal | kitty |
| Bar | Waybar |
| Launchers | fuzzel, nwggrid, d77run |
| Notifications | SwayNotificationCenter |
| Lock screen | swaylock, with Super + T or after 5 minutes idle |
| File manager, mail, browser | PCManFM, Geary, Brave |

## Where to change things

| What | File |
|---|---|
| keys, programs started with the session, keyboard, window rules, layout | `~/.config/river/init` |
| the bar | `~/.config/waybar/config_river.jsonc` and the style files next to it |
| notifications | `~/.config/swaync/` |
| lock screen | `~/.config/swaylock/config` |

Programs started with the session are the `riverctl spawn` lines. `init` runs
when river starts, so log out and in again after changing it (or run a single
`riverctl` command in a terminal to try it right away). The original is in
`/etc/skel/.config/river/init`.

## Keys

**Super** is the modifier.

| Keys | Action |
|---|---|
| Super + Shift + Return | terminal |
| Super + A | fuzzel (application launcher) |
| Super + N | nwggrid (application grid) |
| Super + R | d77run |
| Super + Shift + F | file manager |
| Super + M | mail |
| Super + W | web browser |
| Super + P | screenshot (`grim`) |
| Super + T | lock screen |
| Super + X | power menu |
| Super + Q | close window |
| Super + J / Super + K | focus next / previous window |
| Super + Shift + J / Super + Shift + K | swap with the next / previous window |
| Super + Return | move the window to the main area |
| Super + H / Super + L | shrink / grow the main area |
| Super + Shift + H / Super + Shift + L | one more / one fewer window in the main area |
| Super + arrows | put the main area at the top, right, bottom or left |
| Super + Space | float or tile the window |
| Super + F | full screen |
| Super + 1 … 9 | go to tag |
| Super + Shift + 1 … 9 | move window to tag |
| Super + 0 | show all tags |
| Super + Shift + P | show or hide the scratchpad |
| Super + Shift + O | send the window to the scratchpad |
| Super + . / Super + , | focus the next / previous monitor |
| Super + left / right / middle mouse button | move / resize / float a window |
| Super + F11 | pass all keys to the window (again to return) |
| Super + Shift + E | exit river |

## Keyboard layout

In `init`:

```sh
riverctl keyboard-layout pt
```

## Wallpaper

The line `riverctl spawn "swaybg -i ~/Wallpaper/background1.png"` sets it at
start-up; change the file name to another image in `~/Wallpaper/`.
