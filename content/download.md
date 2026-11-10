+++
title = "Download"
description = "DSlot's card image for the Anbernic RG DS+, how to check it, the release notes, licences and source."
+++

{% set r = config.extra.release %}
{% set nib = config.extra.nibos_site %}
{% if not r.published %}
> [!NOTE]
> DSlot {{ r.version }} isn't published yet.
{% endif %}

## DSlot {{ r.version }}

The second beta, released {{ r.date }}: the PSP, Arcade, Mega-CD, 32X and Pico, the volume
and brightness on screen, and fixes. Everything planned for 0.1.0 is in, and the betas from
here to 0.1.0 bring fixes. For the **Anbernic RG DS+** only. The image is a whole card: DSlot,
its emulators and [nibOS]({{ nib }}/), the streamlined Arch Linux they are based on. Write it to a microSD card
of 16 GB or more with Raspberry Pi Imager or `dd`, or with balenaEtcher once it is unpacked:
[Installing](@/manual/install.md) has every step. A DS+ already running DSlot (0.1.0-alpha1 or
later) can take it as an [update](@/manual/updates.md) instead of a new card.

{{ <release_images release={r} /> }}

Every file of the release, with the release notes, is on its
[GitHub release page]({{ r.url }}). Looking for the system without the game shelf, a Linux
console on the DS+? That is [nibOS]({{ nib }}/download/).

## Checking the download

**`SHA256SUMS`** lists the SHA-256 checksum of every file in the release. Download it beside
your image, then, in that folder:

```sh
sha256sum -c SHA256SUMS --ignore-missing          # Linux
shasum -a 256 -c SHA256SUMS --ignore-missing      # macOS
```

Each file you have should say `OK`. On Windows, `Get-FileHash <file>` in PowerShell prints the
checksum to compare with the cards above. A file that doesn't match: download it again, and
don't write it.

**Signatures.** Releases are signed with the update key, a
[minisign](https://jedisct1.github.io/minisign/) Ed25519 key with key ID
**{{ r.key_id }}**:

```
untrusted comment: minisign public key {{ r.key_id }}
{{ r.public_key }}
```

The same key is in every image (`/usr/lib/nibos/update.pub`) and in the nibOS repository
([`hw/files/usr/lib/nibos/update.pub`](https://github.com/abradburne/nibos/blob/{{ r.tag }}/hw/files/usr/lib/nibos/update.pub)).
What is signed is the image's **update manifest**, which lists the checksum of the update
payload and of every 16 MiB piece of it. A device takes an update only if that signature checks
out. To check a manifest yourself:

```sh
minisign -Vm nibos-{{ r.version }}-rgds-dslot.manifest.json -P {{ r.public_key }}
```

The `.manifest.json`, `.manifest.json.minisig` and `.slot` files are what a device's updater
downloads, and keep their `nibos-…-rgds-dslot` names so that every DS+ already out there finds
them; to write a card, use the `.img.xz`.

## What's in it

- **DSlot 0.6.0**, the game shelf, and the emulators: DSperate (DS, GBA), inkdot (Game Boy,
  Game Boy Color), nibcase 0.3.0 with its emulator cores (SNES, NES, Famicom Disk System, Mega
  Drive, Mega-CD, 32X, Pico, Master System, SG-1000, Game Gear, PC Engine and PC Engine CD,
  PlayStation, PSP, Arcade, Atari Lynx, Neo Geo Pocket, WonderSwan, Game & Watch), inktick (Game & Watch, a preview), and PortMaster
  support (PortMaster itself downloads on first use).
- **[nibOS]({{ nib }}/) {{ r.version }}**, the streamlined Arch Linux for the device that DSlot
  is based on.
- **Not in it**: games and BIOS files. Bring your own.

## Release notes

What changed since 0.1.0-beta2:

- **Folders of games** (DSlot 0.7.1): folders in a console's folder show on the shelf; A opens
  one, B comes back out. `_hidden` folders stay off the shelf, and a leading `_` isn't shown.
- **Start a game fresh**: Select + A starts from boot; the resume point is set aside, not
  deleted. B no longer starts a game.
- **System → Help**: what's new in this release, and short topics on the controls, the menu,
  saves, sleep and charging, Wi-Fi, adding games and the console.
- **nibcase 0.3.2**: a BIOS named `SCPH-5501.BIN` is found; Clear resume state works for every
  nibcase core; PlayStation playlists that name discs from the card's root play.
- **The power key starts the DS+ after a power-off**, and asleep too long it really powers off.

[0.1.0-beta2](https://github.com/abradburne/nibos/releases/tag/v0.1.0-beta2) brought the PSP,
Arcade, Mega-CD, 32X and Pico, and the volume and brightness on screen.
[0.1.0-beta1](https://github.com/abradburne/nibos/releases/tag/v0.1.0-beta1)'s notes are on its
release page: RetroAchievements on seven more systems, DSlot 0.5.0's menu sections, power off
when asleep, deep sleep at 49 mA, and the Mega Drive's buttons as its pad.
The alphas' notes are on their release pages (they were published as nibOS's):
[0.1.0-alpha6](https://github.com/abradburne/nibos/releases/tag/v0.1.0-alpha6),
[0.1.0-alpha5](https://github.com/abradburne/nibos/releases/tag/v0.1.0-alpha5),
[0.1.0-alpha4](https://github.com/abradburne/nibos/releases/tag/v0.1.0-alpha4),
[0.1.0-alpha3](https://github.com/abradburne/nibos/releases/tag/v0.1.0-alpha3),
[0.1.0-alpha2](https://github.com/abradburne/nibos/releases/tag/v0.1.0-alpha2),
[0.1.0-alpha1](https://github.com/abradburne/nibos/releases/tag/v0.1.0-alpha1).

What isn't finished: [Known issues](@/manual/known-issues.md). Every change, day by day:
nibOS's [changelog](https://github.com/abradburne/nibos/blob/{{ r.tag }}/CHANGELOG.md), which
covers the whole image.

## Licences and source

The image carries, on its NIBOS partition:

- `NOTICE`: every component, its version and licence; the non-free firmware named as such;
  the written source offer.
- `packages.txt`: every Arch Linux ARM package in the image, with its version and licence.
- `licenses/`: the licence texts that no package installs.

nibOS's own code is under the GNU GPL, version 3 or later; nibkit and the emulators written for
nibOS are MIT or Apache-2.0 ([Licences](@/licences.md)). Three emulator cores, **Snes9x**,
**FinalBurn Neo** and **PicoDrive**, have non-commercial licences: the DSlot image may not be
sold, or included in anything sold.

**Source code.** The complete corresponding source for the GPL and LGPL software in this
image, and for at least three years after this release was last offered:

| Part | Source |
|---|---|
| nibOS: kernel and U-Boot patches, device tree, hardware layer, tools | [abradburne/nibos](https://github.com/abradburne/nibos/tree/{{ r.tag }}) at `{{ r.tag }}` |
| DSlot | [abradburne/DSlot](https://github.com/abradburne/DSlot/tree/d603d60) at `d603d60` (0.6.0) |
| DSperate | [abradburne/DSperate](https://github.com/abradburne/DSperate/tree/e359292) at `e359292` |
| inkdot | [abradburne/inkdot](https://github.com/abradburne/inkdot/tree/12d5c9b) at `12d5c9b` |
| nibcase | [abradburne/nibcase](https://github.com/abradburne/nibcase/tree/fd417c2) at `fd417c2` (0.3.0) |
| inktick | [abradburne/inktick](https://github.com/abradburne/inktick/tree/e8eeec9) at `e8eeec9` |
| nibkit | [abradburne/nibkit](https://github.com/abradburne/nibkit), at the tag the projects pin, `v0.4.1` |
| Arch Linux ARM packages, the libretro cores | Their source packages, attached to the [release]({{ r.url }}) as `nibos-{{ r.version }}-sources-*.tar.zst`, with `SOURCES.md` saying what is where |

The kernel is mainline Linux at `0fcb05b` with the patches in nibOS's `kernel/`,
`socs/rk3568/kernel/` and `boards/rg-ds-plus/kernel/`; U-Boot is v2026.10 with the patches in
`uboot/`, `socs/rk3568/uboot/` and `boards/rg-ds-plus/uboot/`.
