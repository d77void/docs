# wasp

**wasp** is a Wayland compositor in the style of dwm: windows are tiled
automatically, and workspaces are numbered *tags*. It is a fork of dwl with
its configuration in Lua, read again live, without recompiling. The desktop
shell on top (bar, launcher, lock screen, session menu, wallpaper picker) is
**Utumno**, driven by `qsd77`.

| | |
|---|---|
| Login screen | greetd |
| Terminal | Alacritty |
| Shell (bar, launcher, menus) | Utumno, through `qsd77` |
| Notifications | dunst |
| Run dialog | d77run, and `wmenu-run` as the plain menu |
| Lock screen | Utumno's, with Super + T or after 5 minutes idle |

## Where to change things

Everything is in **`~/.config/wasp/config.lua`**: key bindings, programs
started with the session (`wasp.autostart`), keyboard layout
(`wasp.keyboard`), terminal (`wasp.terminal`), layouts and colours. The file
explains itself and has examples. After saving it, press **Alt + Shift + R**
to apply it, with no need to log out.

The original is in `/etc/skel/.config/wasp/config.lua`.

## Keys

**Alt** is the main modifier (`wasp.modkey`). **Super** (the Windows key) is
used for Utumno's own actions.

| Keys | Action |
|---|---|
| Alt + Shift + Return | terminal |
| Alt + P | menu (`wmenu-run`) |
| Alt + \` (grave) | drop-down terminal |
| Super + Space | application launcher |
| Super + R | d77run |
| Super + T | lock screen |
| Super + X | session menu (log out, reboot, shut down) |
| Super + Y | wallpaper picker |
| Super + A | Ollama chat |
| Alt + Shift + C | close window |
| Alt + J / Alt + K | focus next / previous window |
| Alt + Shift + J / Alt + Shift + K | move window down / up the stack |
| Alt + Return | swap the window into or out of the main area |
| Alt + H / Alt + L | shrink / grow the main area |
| Alt + I / Alt + D | one more / one fewer window in the main area |
| Alt + T / F / M / R | layout: tile / floating / monocle / dwindle |
| Alt + Space | next layout |
| Alt + Shift + Space | float or tile the window |
| Alt + E | full screen |
| Alt + 1 … 9 | go to tag |
| Alt + Shift + 1 … 9 | move window to tag |
| Alt + 0 | show all tags |
| Alt + , / Alt + . | focus the monitor on the left / right |
| Alt + Tab | back to the previous tags |
| Print | screenshot to `~/screenshot-<date>-<time>.png` |
| Alt + Shift + R | reload `config.lua` |
| Alt + Shift + Q | quit wasp |

The drop-down terminal key is the one with `` ` `` on a US keyboard, left of
1. Installations made from ISOs built before 16 October 2026 have it on
Alt + , instead, where it also stops Alt + , from focusing the left monitor;
change `"comma"` to `"grave"` in its `toggle-scratchpad` line to match.

## Idle

After 5 minutes without input the screen locks, after 5.5 it turns off
(any key or mouse movement turns it back on), and it always locks before the
computer suspends. A full-screen video keeps it awake. This is the `swayidle`
entry in `wasp.autostart`; change the numbers of seconds there.

Installations made from ISOs built before 16 October 2026 do not have it. To
add it, install the two programs:

```sh
sudo xbps-install -S swayidle wlopm
```

and add this entry to `wasp.autostart` in `config.lua`, then log out and in
again:

```lua
{ "swayidle", "-w",
  "timeout", "300", "qsd77 -c utumno locker",
  "timeout", "330", "wlopm --off '*'", "resume", "wlopm --on '*'",
  "before-sleep", "qsd77 -c utumno locker" },
```

## Wallpaper

Press **Super + Y** to pick one. Utumno's wallpaper script sets it at start-up
(through `awww`); put your own images in `~/Wallpaper/`.

## Changing the keyboard layout

In `config.lua`:

```lua
wasp.keyboard = {
  layout = "pt",
  ...
}
```

Then **Alt + Shift + R**.
