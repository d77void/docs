# Plasma

**KDE Plasma**, the full desktop, with KDE's applications, configured with
d77void's look.

| | |
|---|---|
| Login screen | SDDM, theme `slice` |
| Browser | LibreWolf (Firefox on musl) |
| Text editor | Kate |
| Drop-down terminal | Yakuake |
| Package manager | OctoXBPS, or `xbps` in Konsole |

## Where to change things

Almost everything is changed in **System Settings**: panel, widgets,
wallpaper, theme, keyboard layout and shortcuts. Plasma writes those choices
into files in `~/.config/` (`kdeglobals`, `kwinrc`,
`plasma-org.kde.plasma.desktop-appletsrc` and others); there is no need to
edit them by hand.

The original files are in `/etc/skel/.config/`.

## Keys

Plasma's own shortcuts apply: for example, the **Super** key opens the
application launcher. Check and change them in
**System Settings → Shortcuts**. d77void adds:

| Keys | Action |
|---|---|
| F12 | show or hide Yakuake (drop-down terminal) |

## Keyboard layout

**System Settings → Keyboard → Layouts**.

## Wallpaper

Right-click the desktop, **Desktop and Wallpaper**. d77void's wallpapers are
in `/usr/share/backgrounds/Wallpaper/`.
