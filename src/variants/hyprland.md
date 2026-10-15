# Hyprland

**Hyprland** is a dynamic tiling Wayland compositor with animations and
rounded corners. In d77void its configuration is written in **Lua**
(`hyprland.lua`).

| | |
|---|---|
| Login screen | greetd |
| Terminal | kitty |
| Bar | Waybar |
| Launchers | fuzzel, nwggrid, d77run |
| Notifications | dunst |
| Lock screen | hyprlock, with Super + T (there is no automatic lock when idle) |
| File manager, mail, browser | PCManFM, Geary, Brave (Firefox on musl) |

## Where to change things

| What | File |
|---|---|
| keys, programs started with the session, keyboard, monitors, look | `~/.config/hypr/hyprland.lua` |
| the bar | `~/.config/waybar/config_hypr.jsonc` and the style files next to it |
| lock screen | `~/.config/hypr/hyprlock.conf` |
| fuzzel launcher and power menu | `~/.config/fuzzel/` |
| wallpaper at start-up | `~/.azotebg-hyprland` |

The programs the keys open are set near the top of `hyprland.lua`:

```lua
local terminal    = "kitty"
local fileManager = "pcmanfm"
local menu        = "fuzzel"
local mail        = "geary"
local web         = "brave-browser-stable"
```

Programs started with the session are the `hl.exec_cmd(...)` lines. Hyprland
applies the file as soon as it is saved. The originals are in
`/etc/skel/.config/hypr/`.

## Keys

**Super** is the modifier (`mainMod`).

| Keys | Action |
|---|---|
| Super + Return | terminal |
| Super + A | fuzzel (application launcher) |
| Super + N | nwggrid (application grid) |
| Super + R | d77run |
| Super + F | file manager |
| Super + W | web browser |
| Super + L | mail |
| Super + T | lock screen |
| Super + X | power menu |
| Super + M | log out |
| Super + Q | close window |
| Super + V | float or tile the window |
| Super + J | change the split direction |
| Super + P | pseudo-tile the window |
| Super + arrows | move focus |
| Super + 1 … 0 | go to workspace |
| Super + Shift + 1 … 0 | move window to workspace |
| Super + S | show or hide the special workspace |
| Super + Shift + S | move window to the special workspace |
| Super + mouse wheel | change workspace |
| Super + left / right mouse button | move / resize a window |

Volume, microphone, brightness and media keys work, also on the lock screen.

## Keyboard layout

In `hyprland.lua`, in the input settings:

```lua
kb_layout  = "pt",
```

## Wallpaper

At start-up, `~/.azotebg-hyprland` sets the wallpaper with `swaybg`. To choose
another one, use **Azote** (included), which saves the image you pick for the
next start-up too, or edit the image path in that file.
