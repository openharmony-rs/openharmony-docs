# SurfaceRotationOptions

```TypeScript
declare interface SurfaceRotationOptions
```

Defines whether the orientation of the surface held by the current **XComponent** is locked when the screen rotates.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## lock

```TypeScript
lock?: boolean
```

Whether the orientation of the surface is locked when the screen rotates. If this parameter is not set, the default value **false** is used, indicating that the orientation is not locked.

**true**: The orientation of the surface is locked when the screen rotates.

**false**: The orientation of the surface is not locked when the screen rotates.

**Type:** boolean

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
