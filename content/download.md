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

The fourth beta, released {{ r.date }}: GBA DS, screen looks for the DS, GBA and Game Boy,
and a low-battery warning. Everything planned for 0.1.0 is in, and the betas from
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

- **DSlot 0.7.1**, the game shelf, and the emulators: DSperate (DS, GBA), GBA DS (GBA games
  with a second screen), inkdot (Game Boy, Game Boy Color), nibcase 0.3.2 with its emulator cores (SNES, NES, Famicom Disk System, Mega
  Drive, Mega-CD, 32X, Pico, Master System, SG-1000, Game Gear, PC Engine and PC Engine CD,
  PlayStation, PSP, Arcade, Atari Lynx, Neo Geo Pocket, WonderSwan, Game & Watch), inktick (Game & Watch, a preview), and PortMaster
  support (PortMaster itself downloads on first use).
- **[nibOS]({{ nib }}/) {{ r.version }}**, the streamlined Arch Linux for the device that DSlot
  is based on.
- **Not in it**: games and BIOS files. Bring your own.

## Release notes

What changed since 0.1.0-beta3:

- **GBA DS**: Game Boy Advance games with their map, race HUD or status screen on the second
  screen, on DSlot's new GBA DS page: the 51 games in `Roms/GBA` that
  [GBA DS](https://github.com/kyannon/gba-ds) 1.5 supports, with their regional releases. Back
  opens nibOS's menu; Menu saves and quits. Saves are kept apart, in `Saves/GBADS/`
  ([GBA DS](@/manual/games.md#gba-ds)).
- **Screen looks**: DS and GBA games (DSperate) get LCD looks (grid, scanlines, soft,
  subpixels) and the GBA's own colours; Game Boy games (inkdot) get a *Screen texture* setting,
  by default like the model's own screen ([Screen looks](@/manual/games.md#screen-looks)).
- **A low-battery warning and a safe power-off**: a notice and a blinking red LED at 10% and
  5%; at 2% the DS+ saves your game and powers off.
- **Asleep too long, the DS+ really powers off**, and a tap of power starts it, also after a
  sleep.
- **Linux 7.3.4**, the stable release, in place of a 7.3 release candidate.

[0.1.0-beta3](https://github.com/abradburne/nibos/releases/tag/v0.1.0-beta3) brought:

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
| DSlot | [abradburne/DSlot](https://github.com/abradburne/DSlot/tree/007a375) at `007a375` (0.7.1 and its GBA DS page) |
| DSperate | [abradburne/DSperate](https://github.com/abradburne/DSperate/tree/d4777cc9) at `d4777cc9` |
| GBA DS | [abradburne/gba-ds](https://github.com/abradburne/gba-ds/tree/fe366b9) at `fe366b9` (nibOS's fork of GBA DS 1.5), with mGBA in the release's source |
| inkdot | [abradburne/inkdot](https://github.com/abradburne/inkdot/tree/227fee9) at `227fee9` |
| nibcase | [abradburne/nibcase](https://github.com/abradburne/nibcase/tree/c2a8fd3) at `c2a8fd3` (0.3.2) |
| inktick | [abradburne/inktick](https://github.com/abradburne/inktick/tree/e8eeec9) at `e8eeec9` |
| nibkit | [abradburne/nibkit](https://github.com/abradburne/nibkit), at the tags the projects pin: `v0.5.0` (DSlot), `v0.4.1` (the emulators) |
| Arch Linux ARM packages, the libretro cores | Their source packages, attached to the [release]({{ r.url }}) as `nibos-{{ r.version }}-sources-*.tar.zst`, with `SOURCES.md` saying what is where |

The kernel is mainline Linux 7.3.4 (`7595a62`) with the patches in nibOS's `kernel/`,
`socs/rk3568/kernel/` and `boards/rg-ds-plus/kernel/`; U-Boot is v2026.10 with the patches in
`uboot/`, `socs/rk3568/uboot/` and `boards/rg-ds-plus/uboot/`.
