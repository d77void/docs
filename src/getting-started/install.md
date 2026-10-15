# Installing

## The live session

Boot the ISO from a USB stick. The live session logs in as the user `anon`
(password `voidlinux`), and opens the installer by itself on ISOs that have
Calamares.

## With Calamares

Most ISOs include **Calamares**, a graphical installer. In the live session
it starts on its own; if you closed it, open it again from the menu.

Calamares asks for the language, keyboard, disk and user, then installs. At
the end it also:

- adds d77void's package repository to the installed system
  (`/etc/xbps.d/d77void-repo.conf`);
- removes itself and its files from the installed system.

The keyboard layout chosen in Calamares is written for X11
(`/etc/X11/xorg.conf.d/00-keyboard.conf`). Wayland compositors read their
own setting; see [Where things are configured](../system/configuration.md#keyboard-layout).

## Without Calamares

ISOs built without Calamares use a text installer:

```sh
sudo d77void-installer
```

Its menu goes through keyboard, network, source, mirror, hostname, locale,
time zone, root password, user account, boot loader, partitions and file
systems, like Void's own `void-installer`. For **Source**, choose **Local**
(packages from the ISO image) to install the live system with its
configuration; **Network** installs only Void's base system.

## After installing

**d77-welcome** opens on every login until you press **Don't show this
again**. Use it to set the root password, update the system and install
common software; see
[Updating and installing software](../system/updates.md).

Then read the page of your variant to learn its shortcuts.
