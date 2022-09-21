# DOS Container manifests

This repository contains build manifests for use with DOS Container. These manifests
combine a disk image, operating system, the game itself and bootup scripts into a
single file that can be used with (primarily) the MiSTer AO486 core, but any other
half-decent MS-DOS emulator should work just as well.

This repository does not contain any copyrighted works from third parties and is not
supposed to do so. These manifests are purely the recipes for doscontainer to work
from. You still need to provide the raw ingredients.

## Work in progress

This repository represents a work in progress. Nothing of what you find here is ready
for prime time in any way as long as DOS Container itself is still in major flux.

While this work is out in the open, you are entirely on your own if you choose to
download it for any purpose.

## Metadata

Games go into the games/ subdirectory, applications go into apps/. Inside these dirs
you'll find a YAML file for each item. This file specifies how doscontainer should
construct the disk image for your specific title.

| Field | Function|
|-------|---------|
| title | Human-readable title for the game or app |
| publisher | The original publisher |
| year | Year the game or app was released |
| artwork | Optional URL that points to a picture of the box. |
| os | msdos622 and none are the only supported values for now. The former installs the full OS, the latter just a bare-bones bootable environment. |
| drivers | Set of standard drivers that must be present on the system. See below. |
| game | URL poiting to the ZIP file of the game. |
| size | Size in bytes for the disk image. This will get rounded to the nearest lower sector-boundary. |
| shortname | Short name for the title, max 8 characters. |

### Drivers

Many DOS games require drivers to be loaded. Expect the options here to grow over time. For now we support:

| Value | Function |
|-------|----------|
| himem | Loads MS-DOS HIMEM.SYS at boot. |
| smartdrv | Loads the SMARTDRV drive caching software. |
| mouse | Loads a tiny MS-compatible mouse driver. |
