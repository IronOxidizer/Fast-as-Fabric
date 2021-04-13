# FastAsFabric

Fast, efficient, and optimized modpack built for minimum lag and maximum performance

This modpack serves as a base for other modpacks, or as a simple solution for maximum performance in vanilla Minecraft. It was inspired by [optifine_alternatives](https://gist.github.com/LambdAurora/1f6a4a99af374ce500f250c6b42e8754) and [fabulously-optimized](
https://www.curseforge.com/minecraft/modpacks/fabulously-optimized) with a focus of validating claims through benchmarks and removing any unnecessary mods. 

## Performance

TODO: Insert tables with normalized results here

## Mods

### Benchmark Verified

Mods that have been verified in our benchmarks to provide measurable performance increase. These are present within the official releases of this mod pack.

- [Sodium](https://www.curseforge.com/minecraft/mc-mods/sodium)
- [Lithium](https://www.curseforge.com/minecraft/mc-mods/lithium)
- [Phosphor](https://www.curseforge.com/minecraft/mc-mods/phosphor)

Depends on:

- [Fabric](https://fabricmc.net/)
- [Fabric API](https://www.curseforge.com/minecraft/mc-mods/fabric-api)

### Verified

Mods that have been verified by us to improve performance outside of our benchmarks in hard to test or niche scenarios. These are present within the official releases of this mod pack.

- [Dynamic FPS](https://www.curseforge.com/minecraft/mc-mods/dynamic-fps)
- [Fat Experience Orbs](https://www.curseforge.com/minecraft/mc-mods/fat-experience-orbs)

### Unverified

Mods that claim to improve performance, but have yet to be verified by us. These are only present within beta releases of this modpack.

- [Krypton](https://www.curseforge.com/minecraft/mc-mods/krypton) (networking optimization)
- [Hydrogen](https://modrinth.com/mod/hydrogen) (performance hacks not suitable for lithium)
- [FerriteCore](https://modrinth.com/mod/ferrite-core) (supposedly better than hydrogen)
- [Fast Redstone](https://modrinth.com/mod/fast-redstone)
- [Enhanced Block Entities](https://modrinth.com/mod/ebe) (requires special setup with sodium)
- [Fast Furnace for Fabric](https://www.curseforge.com/minecraft/mc-mods/fast-furnace-for-fabric)
- [FastBench for Fabric](https://www.curseforge.com/minecraft/mc-mods/fastbench-for-fabric)
- [Simplex Terrain Generation](https://www.curseforge.com/minecraft/mc-mods/simplex-terrain-generation)
- [Cull Leaves](https://www.curseforge.com/minecraft/mc-mods/cull-leaves)
- [EntityCulling](https://www.curseforge.com/minecraft/mc-mods/entityculling)
- [FastChest](https://www.curseforge.com/minecraft/mc-mods/fastchest)
- [No Fade](https://www.curseforge.com/minecraft/mc-mods/no-fade)

### Removed Dependencies

Mods that are not present within this pack due not improving performance, lack of compatibility, or lack of stability.

- [Foam​Fix](https://www.curseforge.com/minecraft/mc-mods/foamfix-optimization-mod) (incompatible version)
- [OptiFabric](https://www.curseforge.com/minecraft/mc-mods/optifabric) (incompatible with Sodium)

## Benchmarking

Raw results are available in the `benchmarks` directory. The following setting were used:

- Launched offline
- Fullscreen
- Max FoV (Quake Pro)
- VSync Off
- Max Framerate Unlimited
- Render distance 10
- Spectator
- Peaceful
- All other settings are left on default unless specified.

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

### Bench world

The bench world is first randomly generated where spawn has a decent amount of trees. It is then filled evenly with various stress blocks in a 3 chunk radius around the desired test location. These blocks are:

- 16 pistons powered by 1 tick comparator clocks
- 64 torches
- 64 cobblestone wall
- 16 smelting furnaces

The player is then moved to a location and angle such that some of the items are not in field of view. Afterwards, entities are spawned 2 blocks above the player using the following commands:

- `/give @p minecraft:repeating_command_block`
- Place wooden button on it repeating command block
- Set command to `summon minecraft:chicken ~ ~2 ~`, press button
- Set command to `summon minecraft:sheep ~ ~2 ~`, press button

After 1 minute of waiting for the entities to settle, time is set to midnight, gamemode switched to spectator, and the world and instance is saved and quit. All benchmarks are done with a fresh copy of the instance and 2 minutes after loading into the world. Once loaded in, the camera and position is never moved, only commands and f3 is used as input.

### Glossary

For all measurements, smaller is better. Each result is relative to the best result for that metric.

**geometric mean**

- each metric is normalize
- an aggregate of all other metrics
- good metric for measuring overall performance

**mean frametime**

- measured in milliseconds
- average time per frame
- 1 / average fps
- good measurement for understanding visual smoothness
- better than FPS for calculating geometric mean

**memory usage**

- measured in megabytes
- +/- 100MB
- single player memory usage reflects server + client memory usage

**mspt**

- measured in milliseconds
- milliseconds per tick
- average time taken to processes a game tick
- `/tick warp 1000`

**kchunk time**

- measured in seconds
- +/- 0.5s
- time taken to generate ~1k chunks minus the already generated chunks
- good measurement of how much lag is generated when exploring
- `/pregen start 16`