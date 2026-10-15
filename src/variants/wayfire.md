# Wayfire

**Wayfire** is a Wayland compositor with visual effects (a 3D desktop cube,
wobbly windows, workspace overview), built from plugins. Windows float by
default, as on a classic desktop; the panel, dock and wallpaper come from
**wf-shell**.

| | |
|---|---|
| Login screen | greetd |
| Terminal | kitty |
| Panel, dock, wallpaper | wf-shell (`wf-panel`, `wf-dock`, `wf-background`) |
| Run dialog | d77run |
| Notifications | dunst |
| Log-out screen | wlogout |
| Lock screen | swaylock, with Super + T or after 5 minutes idle |
| File manager, mail, browser | PCManFM, Geary, Brave |

## Where to change things

| What | File |
|---|---|
| keys, plugins, programs started with the session, keyboard, effects | `~/.config/wayfire.ini` |
| panel, dock and wallpaper | `~/.config/wf-shell.ini` |
| log-out screen | `~/.config/wlogout/` |
| lock screen | `~/.config/swaylock/config` |

**WCM** (Wayfire Config Manager), included, changes `wayfire.ini` from a
window: plugins, key bindings and effects. Wayfire applies changes to
`wayfire.ini` as soon as the file is saved. The originals are in
`/etc/skel/.config/`.

Programs started with the session are in the `[autostart]` section of
`wayfire.ini`; key-to-command bindings are in the `[command]` section, as
pairs such as `binding_terminal = <super> KEY_ENTER` and
`command_terminal = kitty`.

## Keys

| Keys | Action |
|---|---|
| Super (alone) | the panel's application menu |
| Super + Return | terminal |
| Super + R | d77run |
| Super + F | file manager |
| Super + M | mail |
| Super + W | web browser |
| Super + T | lock screen |
| Super + X | log-out screen (wlogout) |
| Super + Q, or Alt + F4 | close window |
| Super + E | overview of all workspaces (then 1 … 9 to pick one) |
| Ctrl + Super + arrows | go to the workspace in that direction |
| Ctrl + Shift + Super + arrows | take the window to the workspace in that direction |
| Super + Left / Right / Up | window to the left half / right half / maximized |
| Super + Down | restore the window's size |
| Alt + Esc | quick switch between windows |
| Ctrl + Super + F | fisheye effect |
| Super + Z | turn the screensaver and screen-off timer on or off |
| Print | screenshot (`grim`) |

Volume and brightness keys work.

## Idle

After 5 minutes without input the screen locks (swaylock, from the `idle =`
line in `[autostart]`), and it always locks before the computer suspends.
Wayfire's own `idle` plugin (`[idle]` in `wayfire.ini`) also starts a
screensaver (the spinning cube) at 5 minutes and turns the screen off at 10;
a full-screen window prevents both, and **Super + Z** switches them off and
on.

On installations made from ISOs built before 16 October 2026 the screen does
not lock by itself. To fix it, replace the `idle =` line in `[autostart]`
with:

```ini
idle = swayidle -w timeout 300 'swaylock -f' before-sleep 'swaylock -f'
```

## Keyboard layout

In the `[input]` section of `wayfire.ini`:

```ini
xkb_layout = pt
```

## Wallpaper

The wallpaper is drawn by `wf-background`, from the `image =` line in the
`[background]` section of `~/.config/wf-shell.ini`
(`/usr/share/Wallpaper/background3.png` at first). Point it at any image,
for example one in `~/Wallpaper/`.
