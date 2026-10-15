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
| Lock screen | hyprlock, with Super + T or after 5 minutes idle (hypridle) |
| File manager, mail, browser | PCManFM, Geary, Brave (Firefox on musl) |

## Where to change things

| What | File |
|---|---|
| keys, programs started with the session, keyboard, monitors, look | `~/.config/hypr/hyprland.lua` |
| the bar | `~/.config/waybar/config_hypr.jsonc` and the style files next to it |
| lock screen | `~/.config/hypr/hyprlock.conf` |
| idle: dim, lock, screen off | `~/.config/hypr/hypridle.conf` |
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

## Idle

`hypridle` dims the screen after 2.5 minutes without input, locks it after
5 and turns it off after 5.5; it also locks before the computer goes to
sleep. Change the times in `hypridle.conf`.

Installations made from ISOs built before 16 October 2026 do not start
`hypridle`. To add it:

1. In **d77-welcome**, add the **Hyprland Repository** if it is not there yet
   (Hyprland's packages come from it).
2. Install it:

   ```sh
   sudo xbps-install -S hypridle
   ```

3. In `~/.config/hypr/hyprland.lua`, inside `hl.on("hyprland.start", ...)`,
   add the line:

   ```lua
   hl.exec_cmd("hypridle")
   ```

   It starts with the next session; to start it now, run `hypridle &` in a
   terminal.

## Keyboard layout

In `hyprland.lua`, in the input settings:

```lua
kb_layout  = "pt",
```

## Wallpaper

At start-up, `~/.azotebg-hyprland` sets the wallpaper with `swaybg`. To choose
another one, use **Azote** (included), which saves the image you pick for the
next start-up too, or edit the image path in that file.
