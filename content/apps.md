+++
title = "Emulators and apps"
description = "The projects on DSlot's card: DSlot, the emulators DSperate, inkdot, nibcase and inktick, the nibkit SDK, and nibOS underneath."
+++

DSlot's card is several projects, each with its own repository, documentation and licence:
the shelf, the emulators, the SDK they are built with, and nibOS, the streamlined Arch Linux
they are based on. They
share one menu,
one set of buttons and one place for saves, through **nibkit**.

<ul class="app-list">
<li>
<h3>DSlot</h3>
<p class="meta">The game shelf · Rust · GPL-3.0-or-later</p>
<p>What the DS+ starts into: your games as carts over a card slot on the touch screen, their boxes, play time and ratings on the top one, a page for each system, the system picker and cards, resume points, and the settings for the device, Wi-Fi and Bluetooth. It also runs on the RG DS+'s stock system, as an app.</p>
<p><a href="https://github.com/abradburne/DSlot">Repository</a> · <a href="https://github.com/abradburne/DSlot#readme">Guide</a></p>
</li>
<li>
<h3>DSperate</h3>
<p class="meta">DS and Game Boy Advance · C++ · GPL-3.0-or-later</p>
<p>A Nintendo DS emulator with a JIT recompiler, written for ARM handhelds. This fork adds a Game Boy Advance mode, 3D at higher resolution on the GPU, frame pacing locked to the DS+'s panels, and the shared menu. The fork is of <a href="https://github.com/beebono/DSperate">beebono's DSperate</a>.</p>
<p><a href="https://github.com/abradburne/DSperate">Repository</a> · <a href="https://github.com/abradburne/DSperate/blob/main/docs/rk3568-port.md">The RG DS+ port</a></p>
</li>
<li>
<h3>inkdot</h3>
<p class="meta">Game Boy and Game Boy Color · Rust · MIT or Apache-2.0</p>
<p>Written from scratch for the DS+: the game at an exact 5× scale on the top screen, the looks of the Game Boy Color, Game Boy, Pocket and Light, save states with their pictures. Its core passes the standard Game Boy test suites in full.</p>
<p><a href="https://github.com/abradburne/inkdot">Repository</a> · <a href="https://github.com/abradburne/inkdot/blob/main/docs/using.md">Guide</a></p>
</li>
<li>
<h3>nibcase</h3>
<p class="meta">A libretro frontend · Rust · MIT or Apache-2.0</p>
<p>Plays libretro emulator cores with the same menu, buttons, saves and pacing as the other emulators: SNES, NES and Famicom Disk System, Mega Drive, Master System, SG-1000, Game Gear, PC Engine and PC Engine CD, PlayStation, Atari Lynx, Neo Geo Pocket, WonderSwan, and Game & Watch across both screens. Each core is a package of its own, under its own licence.</p>
<p><a href="https://github.com/abradburne/nibcase">Repository</a> · <a href="https://github.com/abradburne/nibcase/blob/main/docs/systems.md">Systems, cores and BIOS</a></p>
</li>
<li>
<h3>inktick <small>(preview)</small></h3>
<p class="meta">Game & Watch · Rust · MIT or Apache-2.0</p>
<p>A Game & Watch emulator written from scratch: the Sharp SM510, SM511 and SM512 chips, LCD segments that fade like the real glass, the piezo's sound, and each unit's clock set from the system's. It plays MAME's Game & Watch sets, with their artwork if you have it.</p>
<p><a href="https://github.com/abradburne/inktick">Repository</a> · <a href="https://github.com/abradburne/inktick/blob/main/docs/using.md">Guide</a></p>
</li>
<li>
<h3>nibkit</h3>
<p class="meta">The SDK · Rust (and a C interface) · MIT</p>
<p>What an app on nibOS needs: where the two screens are, the buttons by their printed labels, touch, each screen's brightness, volume, Wi-Fi and Bluetooth, where files go, settings at three levels, and DSlot's menu for any app. The same app builds for nibOS, the stock system or a desktop computer. With a template app and a guide for people and AI agents alike.</p>
<p><a href="https://github.com/abradburne/nibkit">nibkit</a> · <a href="https://github.com/abradburne/nibos/tree/main/sdk/template">Template app</a> · <a href="https://github.com/abradburne/nibos/blob/main/AGENTS.md">App developer's guide</a></p>
</li>
<li>
<h3>nibOS</h3>
<p class="meta">The system underneath · GPL-3.0-or-later</p>
<p>A streamlined Arch Linux for the device, which DSlot is based on.</p>
<p><a href="{{ config.extra.nibos_site }}/">Site</a> · <a href="https://github.com/abradburne/nibos">Repository</a> · <a href="https://github.com/abradburne/nibos/blob/main/docs/architecture.md">Architecture</a> · <a href="https://github.com/abradburne/nibos/blob/main/docs/roadmap.md">Roadmap</a></p>
</li>
</ul>

## Not ours, and welcome

- **[PortMaster](https://portmaster.games)** installs ports of Linux games. DSlot supports it as
  one of its platforms and downloads it on first use ([PortMaster](@/manual/portmaster.md)).
- **The libretro cores** that nibcase plays are their authors' projects, each under its own
  licence: Snes9x, Nestopia UE, BlastEm, Gearsystem, Handy, Beetle PCE Fast, Beetle NeoPop,
  Beetle Cygne, gw-libretro and PCSX ReARMed.

## Writing your own

An app with an `app.toml` in `APPS/` on a card, or installed in `/usr/share/dslot/apps`, appears
on DSlot's Apps page; an emulator describes itself to DSlot with a small file. Start from
[the template app](https://github.com/abradburne/nibos/tree/main/sdk/template), and read
[DSlot's guide to apps](https://github.com/abradburne/DSlot/blob/main/docs/apps.md) and
[to emulators](https://github.com/abradburne/DSlot/blob/main/docs/emulators.md).
