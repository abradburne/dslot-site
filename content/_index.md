+++
title = "DSlot"
template = "index.html"

[extra]
headline = "A replacement OS and game launcher for the RG DS+."
lede = "DSlot runs from its own microSD card. Power on, and about five seconds later your games are on both screens, twenty-three systems behind one menu. The stock card stays as it is: swap it back any time."
stack = [
  { part = "Kernel", what = "Linux 7.3, mainline" },
  { part = "Bootloader", what = "U-Boot, mainline" },
  { part = "Graphics", what = "Panfrost and Mesa" },
  { part = "Userland", what = "Arch Linux ARM" },
]

shots = [
  { src = "dslot-carts.webp", caption = "Carts over the slot", alt = "The shelf: Mole Patrol's box, publisher and play record on the top screen; its cartridge over a card slot on the touch screen, Lantern Tide and Paper Harbor either side." },
  { src = "dslot-grid.webp", caption = "The cover grid", alt = "The cover grid: Mole Patrol's box on the top screen; six game covers in a grid on the touch screen, Mole Patrol highlighted." },
  { src = "dslot-menu.webp", caption = "The menu", alt = "DSlot's menu over Lantern Tide: the Game, DS and System tabs, with Favourite, Rating and Delete saves." },
]
hero_render = { src = "rgds-plus.webp", width = 1440, height = 1444, alt = "An Anbernic RG DS+, open, running DSlot: Mole Patrol's box art on the top screen, its cartridge over the slot on the touch screen." }


[extra.shelf]
title = "Made for two screens"
text = "The top screen shows the game you're on: its box, how long you've played it, your rating. The touch screen holds the library, as cartridges over a card slot, a cover grid or a list. Flick through it, or press Select to change system."
link = "@/manual/shelf.md"
link_text = "The shelf, in the manual"

[extra.menu]
title = "One menu in every emulator"
text = "Back opens the same menu whatever you're playing: six save slots with pictures, settings for the game or the whole system, Wi-Fi and Bluetooth. Menu saves and takes you home, and the next start carries on where you left off."
link = "@/manual/controls.md"
link_text = "Every control"

# The systems, by maker. Twenty-three, plus PortMaster's ports.
[[extra.systems]]
maker = "Nintendo"
names = ["DS", "Game Boy Advance", "Game Boy", "Game Boy Color", "SNES", "NES", "Famicom Disk System", "Game & Watch"]
[[extra.systems]]
maker = "Sega"
names = ["Mega Drive", "Mega-CD", "32X", "Master System", "Game Gear", "SG-1000", "Pico"]
[[extra.systems]]
maker = "Sony"
names = ["PlayStation", "PSP"]
[[extra.systems]]
maker = "NEC"
names = ["PC Engine", "PC Engine CD"]
[[extra.systems]]
maker = "Others"
names = ["Arcade (FinalBurn Neo)", "Neo Geo Pocket", "WonderSwan", "Atari Lynx", "PortMaster ports"]

[[extra.notes]]
title = "Sleep"
text = "Close the lid mid-game and the DS+ sleeps. Open it and carry on; Wi-Fi is back about two seconds later."
[[extra.notes]]
title = "Charging"
text = "Charges while switched off, amber light on. Battery protect stops at about 80% to spare the cell."
[[extra.notes]]
title = "Updates"
text = "Signed updates over Wi-Fi, installed while you play. If one fails to start, it rolls back by itself."
[[extra.notes]]
title = "Wi-Fi and Bluetooth"
text = "Join networks and pair headphones or controllers from the menu. Sound follows the headphone jack."
[[extra.notes]]
title = "Your games card"
text = "DSlot reads the stock Roms/ folders, so the games card you already have works in the second slot."
[[extra.notes]]
title = "A real Linux"
text = "Leave the shelf for a console with a touch keyboard, or SSH in from your computer."

[[extra.steps]]
title = "Download the image"
text = "One file for the DS+, with its checksum."
link = "@/download.md"
[[extra.steps]]
title = "Write it to a card"
text = "With Raspberry Pi Imager or dd. 16 GB or larger."
link = "@/manual/install.md"
[[extra.steps]]
title = "Add games, power on"
text = "Card in TF1, games in Roms/, on it or on a card in TF2."
link = "@/manual/games.md"

+++

Built with AI agents (Claude, in Claude Code), directed by one person and played on a real RG DS+
at every step. [Contributing](@/contributing.md) says how to join in, with or without AI.
