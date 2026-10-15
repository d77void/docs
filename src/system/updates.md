# Updating and installing software

d77void is a regular Void Linux system: software is installed and updated
with **xbps**, from Void's repositories and from d77void's own.

## Updating

```sh
sudo xbps-install -Su
```

Run it again if it says that `xbps` itself was updated first. Graphical
alternatives:

- **OctoXBPS**, a graphical package manager, included in most variants;
  several variants also start its notifier, which tells you when updates are
  available.
- **d77-welcome**, with **Update Software Sources** and **Upgrade Installed
  Packages**; see [below](#d77-welcome).

## Installing and removing software

```sh
xbps-query -Rs <word>          # search
sudo xbps-install -S <package>  # install
sudo xbps-remove -R <package>   # remove, with what it pulled in
```

The [Void Linux Handbook](https://docs.voidlinux.org/xbps/index.html) covers
xbps in full.

## d77void's repository

Packages that Void does not carry (d77void's tools, some window managers and
shells, Calamares) come from d77void's repository on SourceForge. Calamares
adds it during installation, in `/etc/xbps.d/d77void-repo.conf`:

```text
repository=https://sourceforge.net/projects/d77void/files/d77void-repo
```

On musl the address ends in `d77void-musl` instead.

d77-welcome can add two more optional repositories, **Hyprland Repository**
and **Cosmic Repository**, with d77void's packages of those desktops
(`hypr-d77` and `cosmic-d77` on SourceForge).

## d77-welcome

d77-welcome opens on every login until you press **Don't show this again**.
Run it again any time:

```sh
d77-welcome
```

It asks for your password when an action needs administrator rights, and
your user must be in the `wheel` group (administrators).

| Section | What it does |
|---|---|
| Set Root Password | sets a password for the `root` account |
| Update Software Sources | refreshes the package lists (`xbps-install -S`) |
| Upgrade Installed Packages | updates everything (`xbps-install -Su`) |
| Office | LibreOffice, or AbiWord and Gnumeric |
| Media & Graphics | GIMP, DeaDBeeF |
| Bluetooth | installs Bluetooth support and enables its service |
| Browser | Firefox, Chromium |
| Flatpak | installs Flatpak, adds your user to its groups, installs a Flatpak store |
| Steam | installs Steam |
| Hyprland Repository, Cosmic Repository | adds those optional repositories |
| Boot Animation | installs one of d77void's two Plymouth boot animations |

Each action shows the packages and the command it runs before running it.

## Services

Services are managed with runit, as on any Void system:

```sh
sudo sv status /var/service/*            # what is running
sudo ln -s /etc/sv/<name> /var/service/  # enable a service
sudo rm /var/service/<name>              # disable it
```

See the [Void Linux Handbook](https://docs.voidlinux.org/config/services/index.html).
