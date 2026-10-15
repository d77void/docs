# spitfire

**spitfire** is a tiling Wayland compositor in the spirit of dwm, written by
the d77void author, with its whole configuration in one Lua file that is read
again live. The desktop shell on top (launcher, lock screen, session menu,
wallpaper picker, on-screen volume) is **Utumno**, driven by `qsd77`, as on
[wasp](wasp.md).

| | |
|---|---|
| Login screen | greetd |
| Terminal | Alacritty |
| Shell (launcher, menus) | Utumno, through `qsd77` |
| Notifications | dunst |
| Run dialog | d77run |
| Lock screen | Utumno's, with Super + Z or after 5 minutes idle |

## Where to change things

Everything is in **`~/.config/spitfire/config.lua`**: key bindings
(`spitfire.bind`), programs started with the session (`spitfire.autostart`),
keyboard (`spitfire.keyboard`), gaps, borders and colours. After saving it,
press **Super + Shift + R** (or run `spitfirectl reload`) to apply it.

The original is in `/etc/skel/.config/spitfire/config.lua`.

## Keys

**Super** is the main modifier; **Alt** moves windows between workspaces.

| Keys | Action |
|---|---|
| Super + Return | terminal |
| Super + S | drop-down terminal |
| Super + A | application launcher |
| Super + R | d77run |
| Super + X | session menu (log out, reboot, shut down) |
| Super + Y | wallpaper picker |
| Super + Z | lock screen |
| Super + Q | close window |
| Super + J / Super + K | focus next / previous window |
| Super + Shift + J / Super + Shift + K | swap with the next / previous window |
| Super + H / Super + L | shrink / grow the main area |
| Super + I / Super + D | one more / one fewer window in the main area |
| Super + T / F / M | layout: tile / fibonacci / monocle |
| Super + Shift + Space | floating layout |
| Super + Space | next layout |
| Super + 1 … 9 | go to workspace |
| Alt + 1 … 9 | move window to workspace |
| Super + Shift + R | reload `config.lua` |
| Super + Shift + Q | quit spitfire |

The volume keys show Utumno's on-screen volume.

## Idle

ISOs built from 16 October 2026 on start `swayidle` from `spitfire.autostart`:
the screen locks after 5 minutes without input and before the computer
suspends. It needs spitfire 0.5.3 or later (`xbps-query -p pkgver spitfire`);
with an older spitfire, `swayidle` simply exits. Turning the screen off when
idle is not available on spitfire yet.

To add it to an older installation, update the system, install `swayidle`,
and add this line to `spitfire.autostart`, then log out and in again:

```lua
"swayidle -w timeout 300 'qsd77 -c utumno locker' before-sleep 'qsd77 -c utumno locker'",
```

## Keyboard layout

In `config.lua`, the default is the US international layout:

```lua
spitfire.keyboard = { layout = "us", variant = "intl", model = "", options = "", repeat_delay = 600, repeat_rate = 25 }
```

For a Portuguese layout, set `layout = "pt"` and `variant = ""`.

## Wallpaper

Press **Super + Y** to pick one from `~/Wallpaper/`.
