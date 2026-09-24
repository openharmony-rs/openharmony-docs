# SurfaceConfig

```TypeScript
declare interface SurfaceConfig
```

Describes whether the surface held by the **XComponent** is treated as opaque during rendering.

**Since:** 22

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isOpaque

```TypeScript
isOpaque?: boolean
```

Whether the surface held by the **XComponent** is treated as opaque during rendering. If this attribute is not set, the default value **false** is used, indicating that the transparency of the pixels in the content drawn on the surface will be applied during rendering. **true**: yes; **false**: no. Default value: **false**.

**Type:** boolean

**Default:** false

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
