# labwc

**labwc** is a stacking Wayland compositor in the style of Openbox: windows
float and overlap as on a classic desktop, with a right-click menu and window
decorations, configured with XML files.

| | |
|---|---|
| Login screen | greetd |
| Terminal | kitty |
| Bar | Waybar |
| Launchers | fuzzel, nwggrid, d77run |
| Notifications | SwayNotificationCenter |
| Lock screen | swaylock, with Super + T or after 5 minutes idle; screen off after 10 |
| File manager, mail, browser | PCManFM, Geary, Brave |

## Where to change things

All of labwc's own files are in `~/.config/labwc/`:

| File | What it holds |
|---|---|
| `rc.xml` | key and mouse bindings, theme, touchpad |
| `autostart` | programs started with the session, idle and lock settings |
| `environment` | environment variables, including the keyboard layout |
| `menu.xml` | the menu shown with a right click on the desktop |
| `themerc` | window decoration colours |

| Other | File |
|---|---|
| the bar | `~/.config/waybar/config_labwc.jsonc` and the style files next to it |
| notifications | `~/.config/swaync/` |
| lock screen | `~/.config/swaylock/config` |

`labwc-tweaks-qt`, included, changes the theme and other settings from a
window. To apply changes to `rc.xml` or `menu.xml`, log out and in again, or
run `labwc --reconfigure`. The originals are in `/etc/skel/.config/labwc/`.

On every login `~/.lmu` rebuilds `menu.xml` from the installed applications
(`labwc-menu-generator`), so edits to `menu.xml` are replaced; to keep a
hand-made menu, remove the `./.lmu &` line from `autostart`.

## Keys

**Super** is shown as `W-` in `rc.xml`.

| Keys | Action |
|---|---|
| Super + Return | terminal |
| Super + A | fuzzel (application launcher) |
| Super + N | nwggrid (application grid) |
| Super + R | d77run |
| Super + F | file manager |
| Super + M | mail |
| Super + W | web browser |
| Super + B | random wallpaper from `~/Wallpaper/` |
| Super + P | screenshot (`grim`) |
| Super + T | lock screen |
| Super + X | power menu |

labwc's own default bindings also apply, for example **Alt + Tab** to switch
windows and **Alt + F4** to close one.

## Keyboard layout

In `~/.config/labwc/environment`:

```text
XKB_DEFAULT_LAYOUT=pt
```

Log out and in again to apply it.

## Wallpaper

The `swaybg` line in `autostart` sets `~/Wallpaper/background1.png` at
start-up; change the file name to use another image. **Super + B** picks a
random one from `~/Wallpaper/` for the current session.

## Weather in the bar

Waybar's weather module, `~/.config/waybar/wittr.sh`, asks wttr.in for the
weather at latitude 41.6, longitude −8.62 (Porto, Portugal); change the two
numbers in it to your own location.
