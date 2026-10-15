# What d77void is

d77void is **Void Linux** with a window manager or desktop already set up:
packages chosen, configuration files written, wallpapers, a login screen and
a few helper tools. Underneath it is a regular Void installation: `xbps`,
runit, and the Void repositories, plus d77void's own repository for a few
extra packages.

## Variants

Each variant is a separate ISO built around one window manager or desktop:

| Kind | Variants | Login screen |
|---|---|---|
| Wayland compositors | hyprland, labwc, mango, niri, river, scroll, somewm, spitfire, sway, wasp, wayfire | greetd |
| Wayland with a ready-made shell | fabric, helium, hypr-dms, hypr-noctalia, mango-dms, mango-noctalia, niri-dms, niri-noctalia, qsd77 | greetd |
| X11 window managers | awesome, bspwm, dwm, fluxbox, herbstluftwm, i3wm, jwm, leftwm, openbox, pwm, qtile, wmd77 | SDDM |
| Desktops | cosmic, gnome, lxqt, plasma, xfce | depends on the desktop (SDDM on Plasma) |
| Minimal | base | text console |

These pages currently cover [wasp](../variants/wasp.md),
[Plasma](../variants/plasma.md), [Sway](../variants/sway.md),
[niri](../variants/niri.md) and [Hyprland](../variants/hyprland.md); more
variants will follow.

d77void can be built for **glibc** (`x86_64`) and **musl** (`x86_64-musl`).
glibc builds come with Brave (LibreWolf on Plasma); musl builds with Firefox.

## What every variant has

- **The d77void identity:** `/etc/os-release` says `d77void GNU/Linux`, with
  `ID_LIKE=void`.
- **d77-welcome**, a small graphical helper shown after installation, for
  common tasks: setting the root password, updating, installing an office
  suite, a browser, Flatpak, Steam, Bluetooth and more. See
  [Updating and installing software](../system/updates.md#d77-welcome).
- **A ready configuration in your home**, copied from the image when your user
  is created. See [Where things are configured](../system/configuration.md).
- **d77run**, a quick run dialog, bound to a key in most variants.
- **runit** services, as on any Void system.

## How it differs from installing Void yourself

| | Plain Void | d77void |
|---|---|---|
| Base system | the same | the same |
| Desktop | you install and configure it | installed and configured |
| Installer | `void-installer` (text) | Calamares (graphical), or `d77void-installer` (text) on the ISOs without Calamares |
| Extra repository | none | d77void's, for packages Void does not carry |

Everything else, such as `xbps-install`, runit services and the Void
Handbook, works as on plain Void.
