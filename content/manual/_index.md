+++
title = "The DSlot manual"
description = "Installing DSlot on the RG DS+, the game shelf, controls, games and saves, the radios, power, updates and what to do when something goes wrong."
sort_by = "weight"
template = "manual.html"
page_template = "manual.html"
+++

This manual is for people who play on DSlot on an **Anbernic RG DS+**: installing it, playing
on it, and getting out of trouble. It covers {{ config.extra.release.version }}.

DSlot is a game shelf on both screens, with emulators for the DS, Game Boy Advance, Game Boy and
Game Boy Color, and through **nibcase** a dozen more systems. It comes as a whole card, and is based on
[nibOS]({{ config.extra.nibos_site }}/), a streamlined Arch Linux for the device (which is why the card's partitions are named
NIBOS). You can leave the shelf for a Linux console any time ([The console](@/manual/console.md)).

What a word means here:

| Word | Means |
|---|---|
| TF1, TF2 | The DS+'s two microSD slots. TF1 (marked TF1/INT) is the one the device starts from. |
| The shelf | DSlot's main screen: your games as carts, boxes or a list. |
| NIBOS-DATA | The card's games partition: games, BIOS files, saves. It is what a computer shows when the card is in its reader. |
| NIBOS | A small partition on the card with the licences, a README and, if you want SSH, the settings file `provision.toml`. |
| Back, Menu | Two of the DS+'s buttons, named as on the device. In a game, Back opens the game's menu and Menu saves and goes back to the shelf. |
