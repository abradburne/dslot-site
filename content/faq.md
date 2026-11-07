+++
title = "Questions"
description = "Common questions about DSlot: devices, safety, games, the stock system, updates, nibOS and AI."
+++

## What is DSlot?

A game system for the **Anbernic RG DS+**: a game shelf on both screens, and emulators for
eighteen systems behind one menu, with the same buttons, saves and settings everywhere. It comes
as a whole card that the DS+ starts from.

## And what is nibOS?

A streamlined Arch Linux for the RG DS+, which DSlot is based on. It is on DSlot's card
already; there is nothing else to install. More on [nibOS's site]({{ config.extra.nibos_site }}/).

## Which devices does it run on?

The **Anbernic RG DS+**, for now.

## Can installing it harm my DS+?

No. DSlot lives entirely on its own card and never touches the device. Put the stock card back
and you're on stock again.

## Do I lose the stock system?

No. Write DSlot to a card of its own and keep your stock card as it is.

## Does it come with games?

No. Bring your own, or try the free homebrew made for these systems.

## Which systems does it play?

DS, Game Boy Advance, Game Boy, Game Boy Color, SNES, NES, Famicom Disk System, Mega Drive,
Master System, SG-1000, Game Gear, PC Engine and PC Engine CD, PlayStation, Atari Lynx, Neo Geo
Pocket, WonderSwan and Game & Watch, and PortMaster's ports. The folders and file types for each
are in [Games, BIOS and saves](@/manual/games.md).

## Can I use my existing games card?

Yes. DSlot uses the same `Roms/` folders as the stock system, so a games card works as it is in
TF2, as long as it is exFAT and labelled `DS`; so does a card set up for slot CFW. Saves made by
other emulators may need copying across: battery saves carry over, save states don't.

## Is it fast?

A picture on both screens 1.5 seconds after the power button, the shelf at about 5 seconds; a
game from the shelf in about 2 seconds, and back in under one.

## How long does the battery last?

It depends on what you play and how bright the screens are. Wi-Fi off, a lower brightness
and closing the lid between sessions all stretch it.
[Sleep, charging and the battery](@/manual/power.md).

## How do I update it?

Over Wi-Fi: DSlot's menu → **Update**. An update replaces the card's whole system in one piece
and keeps your games, saves and settings; if the new version doesn't start, the DS+ goes back to
the old one by itself. [Updates](@/manual/updates.md).

## Is there a Linux system underneath?

Yes: nibOS, a streamlined Arch Linux. Leave the shelf with **Select + Start** for a
console with a touch keyboard, or log in over SSH ([The console](@/manual/console.md)).

## Can I write apps for it?

Yes. nibkit, the SDK, gives an app both screens, the buttons, touch, brightness, sound and
settings, and DSlot's menu; a template app runs on the device as it is. See
[Emulators and apps](@/apps.md#writing-your-own).

## Was it made with AI?

Yes. DSlot, the emulators and nibOS were written by AI agents (Claude, in Claude Code),
directed by one person and played on a real RG DS+ throughout. Contributions made with AI are
welcome ([Contributing](@/contributing.md)).

## Where do I report a bug?

On the issue tracker of the project it's in; if you aren't sure which,
[DSlot's](https://github.com/abradburne/DSlot/issues). Include the log from the card:
[Reporting a bug](@/manual/troubleshooting.md#reporting-a-bug).
