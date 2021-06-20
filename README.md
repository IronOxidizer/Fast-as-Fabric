# Fast as Fabric

Fast, efficient, and optimized Fabric modpack built for minimum lag and maximum performance

![](benchmarks/1.16.5-a-rdp.png)

This modpack serves as a base for other modpacks, or as a simple solution for maximum performance in vanilla Minecraft. It was inspired by [optifine_alternatives](https://gist.github.com/LambdAurora/1f6a4a99af374ce500f250c6b42e8754) and [fabulously-optimized](
https://www.curseforge.com/minecraft/modpacks/fabulously-optimized) with a focus of validating claims through benchmarks and removing unnecessary mods. 

Try it out here: https://www.curseforge.com/minecraft/modpacks/fast-as-fabric

## Mods

### Verified

Included mods that have been verified in our benchmarks to provide at least a 10% overall performance uplift or 5% in any specific scenario.

- [Fat Experience Orbs](https://www.curseforge.com/minecraft/mc-mods/fat-experience-orbs)
- [FerriteCore](https://www.curseforge.com/minecraft/mc-mods/ferritecore)
- [Starlight](https://github.com/Spottedleaf/Starlight)
- [Hydrogen](https://modrinth.com/mod/hydrogen)
- [Lithium](https://www.curseforge.com/minecraft/mc-mods/lithium)
- [Sodium](https://www.curseforge.com/minecraft/mc-mods/sodium) (client only)
- [No Fade](https://www.curseforge.com/minecraft/mc-mods/no-fade) (client only)
- [EntityCulling](https://www.curseforge.com/minecraft/mc-mods/entityculling) (client only)

Depends on:

- [Fabric](https://fabricmc.net/)
- [Fabric API](https://www.curseforge.com/minecraft/mc-mods/fabric-api)
- [Indium](https://github.com/comp500/Indium) (client only)
- [Mod Menu](https://www.curseforge.com/minecraft/mc-mods/modmenu) (client only, optional)
- [Jumploader](https://www.curseforge.com/minecraft/mc-mods/jumploader) (client only, required by curse)

### Unverified

Mods that claim to improve performance, but have yet to be verified by us. These are in consideration to be added but require further testing.

- [Recipe Cache](https://www.curseforge.com/minecraft/mc-mods/recipe-cache) (replaces fast bench + fast furnace)
- [Lazy DFU](https://www.curseforge.com/minecraft/mc-mods/lazydfu)
- [Krypton](https://www.curseforge.com/minecraft/mc-mods/krypton)
- [C2ME](https://github.com/ishlandbukkit/C2ME-fabric)
- [Sodium Extra](https://www.curseforge.com/minecraft/mc-mods/sodium-extra) (client only)
- [Dashloader](https://www.curseforge.com/minecraft/mc-mods/dashloader) (client only)
- [Client Side Noteblocks](https://www.curseforge.com/minecraft/mc-mods/client-side-noteblocks) (client only)

### Extras

Mods that have been proven to increase performance but they apply in a way that most people may not want or expect. These are not included in the modpack.

- [Overworld Two](https://www.curseforge.com/minecraft/mc-mods/overworld-two)
    - completely changes vanilla terrain generation
- [Enhanced Block Entities](https://modrinth.com/mod/ebe) (client only)
    - depends on Indium which currently lacks official build releases
- [Smoke Suppression](https://www.curseforge.com/minecraft/mc-mods/smoke-suppression) (client only)
    - not applicable on lowest settings
- [Cull Leaves](https://www.curseforge.com/minecraft/mc-mods/cull-leaves) (client only)
    - not applicable on lowest settings

### Removed

Mods that are not present within this pack due to inferiority, lack of compatibility, or lack of stability.

- [Simplex Terrain Generation](https://www.curseforge.com/minecraft/mc-mods/simplex-terrain-generation)
    - inferior to Overworld Two
- [Fast Furnace](https://www.curseforge.com/minecraft/mc-mods/fast-furnace-for-fabric)
    - inferior to Recipe Cache and Enhanced Block Entities
- [FastBench](https://www.curseforge.com/minecraft/mc-mods/fastbench-for-fabric)
    - inferior to Recipe Cache
- [Phosphor](https://www.curseforge.com/minecraft/mc-mods/phosphor)
    - inferior to Starlight
- [Foam​Fix](https://www.curseforge.com/minecraft/mc-mods/foamfix-optimization-mod)
    - incompatible version
- [OptiFabric](https://www.curseforge.com/minecraft/mc-mods/optifabric) (client only)
    - incompatible with Sodium
- [FastChest](https://www.curseforge.com/minecraft/mc-mods/fastchest) (client only)
    - inferior to Enhanced Block Entities
- [Better Beds](https://www.curseforge.com/minecraft/mc-mods/better-beds) (client only)
    - inferior to Enhanced Block Entities
- [No Weather Effects](https://www.curseforge.com/minecraft/mc-mods/no-weather-effects) (client only)
    - inferior to Sodium Extras
- [Dynamic FPS](https://www.curseforge.com/minecraft/mc-mods/dynamic-fps) (client only)
    - slows down texture loading

## Benchmarking

Raw results are available in the `benchmarks` directory. The following setting were used:

- launched offline
- fullscreen
- max FoV (Quake Pro)
- vsync off
- max framerate unlimited
- render distance 8
- spectator
- peaceful
- all other settings are set to lowest unless specified.

Benchmarking was done using the following tools:

- [MultiMC](https://multimc.org)
- [Carpet](https://www.curseforge.com/minecraft/mc-mods/carpet)
- [Fabric Chunk Pregenerator](https://www.curseforge.com/minecraft/mc-mods/chunk-pregenerator-fabric)

Testing methodology and data presentation inspired by:

- [Phoronix](https://www.phoronix.com)
- [Gamers Nexus](https://www.gamersnexus.net)
- [Krausest Web UI Framework Benchmark](https://krausest.github.io/js-framework-benchmark)
- [TechEmpower Web Framework Benchmark](https://www.techempower.com/benchmarks)

### Hardware

- Intel i7 6700
- Nvidia GTX 1060 3GB
- 16GB DDR4 (4GB allocated)

### Standard Bench

The bench world is first randomly generated where spawn has a decent amount of trees. It is then filled evenly with various stress blocks in a 3 chunk radius around the desired test location. These blocks are:

- 16 pistons powered by 1 tick comparator clocks
- 64 torches
- 64 cobblestone wall
- 16 smelting furnaces
- 64 chests

The player is then moved to a location and angle such that some of the items are not in field of view. Afterwards, entities are spawned 2 blocks above the player using the following commands:

- `/give @p minecraft:repeating_command_block`
- Place wooden button on it repeating command block
- Set command to `summon minecraft:chicken ~ ~2 ~`, press button
- Set command to `summon minecraft:sheep ~ ~2 ~`, press button

After 1 minute of waiting for the entities to settle, time is set to midnight, gamemode switched to spectator, and the world and instance is saved and quit. All benchmarks are done with a fresh copy of the instance and 2 minutes after loading into the world. Once loaded in, the camera and position is never moved, only commands and f3 is used as input.

### Glossary

**rdp**

- relative delta percentage
- measurement / baseline - 1 * 100%

**fps**

- average frames per second
- measurement of understanding visual smoothness

**tps**

- average ticks per second
- measurement of server smoothness and responsiveness
- `/tick warp 10000`

**cgps**

- average chunks generated per second
- measurement of server and world generation smoothness while exploring
- manually timed
- =10000/(time)
- `/pregen start 50`

**ram**

- memory usage in MB
- singleplayer reflects client + server usage

**rdp sum**

- sum of relative deltas as a percentage
- used to determine overall impact of the mod

## Notes

- Sodium entity culling is disabled as it's done more aggressively by the EntityCulling mod
- Add EBE-supported blocks to entity culling config whitelist to avoid extra path tracing

Additional settings to improve server performance:

- in game `/gamerule disableElytraMovementCheck true`
- in server.properties `allow-flight=true`
- in server.properties `use-native-transport=true` use only on Linux servers
- in server.properties `view-distance=8` less than 8 can affect mob despawn behavior