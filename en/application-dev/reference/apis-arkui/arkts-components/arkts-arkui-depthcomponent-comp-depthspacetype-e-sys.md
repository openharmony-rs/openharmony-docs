# DepthSpaceType (System API)

```TypeScript
declare enum DepthSpaceType
```

Enumerates depth space types.

> **NOTE:** 
> 
> In global mode, other processes reuse the background, depth map, camera parameters, and lighting parameters of the
> wallpaper process, and these cannot be customized.

**Since:** 26.0.0

<!--Device-unnamed-declare enum DepthSpaceType--><!--Device-unnamed-declare enum DepthSpaceType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## GLOBAL

```TypeScript
GLOBAL = 1
```

Global mode, which uses the global background, depth map, camera parameters, and lighting parameters.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-DepthSpaceType-GLOBAL = 1--><!--Device-DepthSpaceType-GLOBAL = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## INSTANCE

```TypeScript
INSTANCE = 0
```

Instance mode, which uses the background, depth map, camera parameters, and lighting parameters of the current process.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-DepthSpaceType-INSTANCE = 0--><!--Device-DepthSpaceType-INSTANCE = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
