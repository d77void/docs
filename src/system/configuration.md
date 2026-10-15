# Where things are configured

## Your configuration is in your home

Each variant's configuration ships in the image as a template, in
`/etc/skel`. When a user is created, the template is copied into that user's
home, and from then on **the copy in your home is the one that counts**:

| What | Where |
|---|---|
| the window manager or compositor | `~/.config/<name>/`, see your variant's page |
| the bar (Waybar, on the variants that use it) | `~/.config/waybar/` |
| notifications (SwayNotificationCenter) | `~/.config/swaync/` |
| application launcher and power menu (fuzzel) | `~/.config/fuzzel/` |
| wallpapers | `~/Wallpaper/` |
| d77-welcome and a few start-up commands, run at each login until d77-welcome's **Don't show this again** deletes it | `~/.auto.sh` |

Editing a file in `/etc/skel` changes nothing for users that already exist;
it only affects users created afterwards. To start over with a variant's
original file, copy it from `/etc/skel` into your home again, for example:

```sh
cp /etc/skel/.config/sway/config ~/.config/sway/config
```

## Keyboard layout

The installer writes the layout you chose for X11
(`/etc/X11/xorg.conf.d/00-keyboard.conf`), which X11 window managers use.
Wayland compositors take it from their own configuration file instead; each
variant's page says where. For example, a Portuguese layout:

| Compositor | Setting |
|---|---|
| Sway | `xkb_layout "pt"` in the `input type:keyboard` block |
| niri | `layout "pt"` in the `xkb` block |
| Hyprland | `kb_layout = "pt"` |
| wasp | `layout = "pt"` in `wasp.keyboard`, in `~/.config/wasp/config.lua` |

## Wallpapers

The variants pick their wallpapers from `~/Wallpaper/` (also in
`/usr/share/Wallpaper/`). Put your own images there. How a variant sets or
changes the wallpaper is on its page; two helpers are shared:

| Command | What it does |
|---|---|
| `wswap-way` | sets a random image from `~/Wallpaper/` with `swaybg` (Wayland) |
| `wswap-X` | the same with `feh` (X11) |

## Web browser

Key bindings, menus and bars open the browser through `d77-browser`, which
runs whichever one is installed: Brave on glibc builds, LibreWolf on Plasma,
Firefox on musl builds (ISOs built from 16 October 2026 on). To make those
keys open another browser, change the command in your variant's configuration
from `d77-browser` to the one you want, for example `firefox`.

## Power menu

Most Wayland variants use `fuzzel-power-menu` (suspend, log out, reboot, shut
down; reboot and shut down ask for confirmation). The X11 variants with dmenu
use `power_menu`. Both use `loginctl`, so they work in any window manager.

## Night light

Several variants start `wlsunset` with the location of Porto, Portugal
(latitude 41.6, longitude −8.62), to warm the screen colours at night. Change
the numbers in the line that starts it, in your variant's configuration, to
your own location.

## Login screen

| Variants | Login screen | Configuration |
|---|---|---|
| Wayland compositors and shells | greetd, with a Quickshell greeter | `/etc/greetd/config.toml` and `/etc/greetd/quickshell-d77/` |
| X11 window managers, Plasma | SDDM, theme `slice` | `/etc/sddm.conf.d/sddm.conf` |
