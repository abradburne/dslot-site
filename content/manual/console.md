+++
title = "The console"
description = "The Linux console under the shelf: the touch keyboard, SSH, copying files and installing software."
weight = 10
+++

DSlot is based on [nibOS]({{ config.extra.nibos_site }}/), a streamlined Arch Linux for the device. The console is a way
into it.

## Getting to the console

- Leave DSlot with **Select + Start**. To go back to the shelf, restart
  (`sudo reboot`). The safe mode's **Open a console** leads here too.
- **Over SSH**, from a computer (below).

On the DS+'s screens, the console is on the top screen and a touch keyboard on the bottom one.
The buttons type too; **Menu + X** hides the keyboard and shows it again. Every key is in
[Controls](@/manual/controls.md#in-the-console-keyboard-on-the-bottom-screen).

The user is called `nibos`. With no password set in `provision.toml`, the console logs in by
itself and `sudo` asks for nothing; with one, both ask for it.

> [!WARNING]
> With no password, anyone holding the DS+ has full control of it. Set one in
> `provision.toml`, or with `passwd` in the console, before you take it anywhere that matters.

## SSH

SSH is off until `provision.toml` gives it a public key; there is no password login over SSH.
With a key given and Wi-Fi on, from a computer on the same network:

```sh
ssh nibos@nibos.local
```

`nibos.local` is the DS+'s name on the local network. If your computer doesn't find it, use the
DS+'s address instead (`ip addr` in the console shows it).

Wi-Fi has to be on: on a fresh card it is off unless `provision.toml` named a network. Turn it
on in DSlot's menu; it stays on.

## Copying files

With SSH, any program that speaks SFTP or SCP copies files to and from the DS+: `scp` in a
terminal, or a file manager that connects over SFTP. Games go in `/mnt/roms/Roms/<folder>`
(NIBOS-DATA) or `/mnt/ds/Roms/<folder>` (the card in TF2):

```sh
scp "My Game.gba" nibos@nibos.local:/mnt/roms/Roms/GBA/
```

DSlot notices them by itself.

## Installing software

Underneath is Arch Linux ARM, so `sudo pacman -S <package>` installs from Arch Linux ARM's
repositories. Worth knowing:

- The card's own packages (its kernel, graphics, DSlot and the emulators) are built for the
  DS+ and aren't in a repository yet. Don't replace them from Arch Linux ARM's
  (`mesa`, for one).
- A full system upgrade (`pacman -Syu`) moves you onto packages DSlot hasn't been tested with.
  It usually works; if it doesn't, write the image again ([Updates](@/manual/updates.md)).
- **An update replaces the whole system**, so packages you installed with `pacman`, and any
  other change to the system's files outside your home folder, are gone after it. Keep what
  you need in your home folder, which is kept, and install packages again after an update.

## More

For more on the system itself, see [nibOS]({{ config.extra.nibos_site }}/).
