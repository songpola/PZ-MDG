# Mod Structure

## Table of Contents

- [Back to Index](/README.md)
- [Overview](#overview)
- [mod.info](#modinfo)
- [media/](#media)
  - [media/scripts/](#mediascripts)
  - [media/models/](#mediamodels)
  - [media/textures/](#mediatextures)
  - [media/sound/](#mediasound)
    - [media/lua/](#medialua)
    - [media/lua/shared/](#medialuashared)
    - [media/lua/client/](#medialuaclient)
    - [media/lua/server/](#medialuaserver)

## Overview

This section contains a brief description of the file and folder structure that makes up a mod. Your mod may include other folders in addition to these, but these ones are the most common.

## `mod.info`

This file can be created/edited with any text editor. It contains details like your mod's ID, name, description, preview image etc.

### Fields: (`*required*`)

- `*name*`: A display name of the mod, shown in the in-game mod selector.
- `*id*`: A unique identifier, used to identify the mod by the game.
- `url`: **_TODO: TBA_**
- `poster`: A name of cover image file of the mod, shown in the in-game mod selector. Can be specify multiple times.
- `description`: A description shown in the mod selector. Can be specified multiple times.
  - All lines will be merged into one and will be displayed in full text.
  - Can be formatted. For more info, refer to the file `..\lua\client\ISUI\RichTextLayout.lua`
- `require`: A list of required mods' `id` that need to be enabled with the mod. Separated by a comma. Will be automatically enabled when enable the mod.
- `pack`: Should contain the name of the`.pack` file.
  - For more info, refer to <https://theindiestone.com/forums/index.php?/topic/8790-custom-texture-packs-and-tile-definitions/>
  - _(Can have multiple?)_
- `type`: for when the pack contains item icons or UI textures.
  - As of writing, There's only `type=ui` value.
  - These packs should be before other packs.
  - _(Can have multiple?)_
- `tiledef`: Should contain the name of the `.tiles` file and a unique number between 100 and around 8000. Separated by a space.
  - The number should be unique to not conflict with other mods!
  - _(Can have multiple?)_
- `versionMin` and `versionMax`: Specify the game version range that this mod can be enabled
  - Both fields follow the same format: `XX.YY Text`
  - The `Text` is an optional note and can be formatted like the description field.

### Example (without `type`)

```text
name=My First Mod
id=MyFirst

url=https://theindiestone.com/forums/

poster=poster.png
poster=poster2.png

description=This is an example mod, <LINE> with two lines of description!

require=otherModA,otherModB

pack=myTexturePack
tiledef=myTileDefinitions 428

versionMin=41.50 - IWBUMS
versionMax=41.55 - IWBUMS
```

## `media/`

The actual content of your mod will be placed in subfolders of the this `media` folder

## `media/scripts/`

This folder contains text files with item, vehicles and recipe definitions. See the section on [Scripts](/scripts/README.md) for more information.

## `media/models/`

Used for 3D models of weapons, vehicles etc.

## `media/textures/`

Icons, 3D model textures and the like go in here, in `.png` format. Pay attention to the naming scheme: Item icons should use the `Item_` prefix.

## `media/sound/`

Sound files go in here, in `.wav` or `.ogg` format.

## `media/lua/`

If your mod includes any .lua scripts, you will need this folder as well as at least one of the subfolders listed below. Any .lua files need to go in the subfolders, not directly in this one.

## `media/lua/shared/`

Used for lua scripts shared by client and server-side logic. These are the first Lua scripts that get loaded.

## `media/lua/client/`

Used for client-side scripts. UI elements, context menus timed actions and the like. These get loaded after any 'shared' lua scripts.

## `media/lua/server/`

Used for server-side scripts. Item spawning, core farming, weather and other server-side events. These only get loaded when the game is actually started (loading a save, starting a server, etc).

## Reference

- [Setting up the mod.info file: a link to a post on TIS Discord explaining how.](https://discord.com/channels/136501320340209664/232196827577974784/901629291274575883)
- <https://pzwiki.net/wiki/Mod_structure>
