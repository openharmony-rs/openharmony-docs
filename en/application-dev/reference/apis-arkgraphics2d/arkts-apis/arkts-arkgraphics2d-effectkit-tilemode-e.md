# TileMode

```TypeScript
enum TileMode
```

Enumerates the tile modes of the shader effect.

> **NOTE:** 
> 
> Under CPU rendering, the shader tile mode supports only DECAL.
> Under GPU rendering, DECAL, CLAMP, REPEAT, and MIRROR modes are all supported.

**Since:** 14

<!--Device-effectKit-enum TileMode--><!--Device-effectKit-enum TileMode-End-->

**System capability:** SystemCapability.Multimedia.Image.Core

## CLAMP

```TypeScript
CLAMP = 0
```

Replicates the edge color if the shader effect draws outside of its original boundary.

**Since:** 14

<!--Device-TileMode-CLAMP = 0--><!--Device-TileMode-CLAMP = 0-End-->

**System capability:** SystemCapability.Multimedia.Image.Core

## DECAL

```TypeScript
DECAL = 3
```

Renders the shader effect only within the original boundary.

**Since:** 14

<!--Device-TileMode-DECAL = 3--><!--Device-TileMode-DECAL = 3-End-->

**System capability:** SystemCapability.Multimedia.Image.Core

## MIRROR

```TypeScript
MIRROR = 2
```

Repeats the shader effect in both horizontal and vertical directions, alternating mirror images so that adjacent images always join.

**Since:** 14

<!--Device-TileMode-MIRROR = 2--><!--Device-TileMode-MIRROR = 2-End-->

**System capability:** SystemCapability.Multimedia.Image.Core

## REPEAT

```TypeScript
REPEAT = 1
```

Repeats the shader effect in both horizontal and vertical directions.

**Since:** 14

<!--Device-TileMode-REPEAT = 1--><!--Device-TileMode-REPEAT = 1-End-->

**System capability:** SystemCapability.Multimedia.Image.Core
