# XComponentExtraFlag (System API)

```TypeScript
declare enum XComponentExtraFlag
```

Defines the extra flags for XComponent.

**Since:** 26.1.0

<!--Device-unnamed-declare enum XComponentExtraFlag--><!--Device-unnamed-declare enum XComponentExtraFlag-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## ENABLE_SOLID_COLOR

```TypeScript
ENABLE_SOLID_COLOR = 0x01
```

Enables the RenderService to create a solid color layer for the XComponent. The size of the solid color layer matches the XComponent's own dimensions, and the color is determined by the XComponent's backgroundColor property. If backgroundColor is not set, the default solid color is black. Once this flag is set, it cannot be updated.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-XComponentExtraFlag-ENABLE_SOLID_COLOR = 0x01--><!--Device-XComponentExtraFlag-ENABLE_SOLID_COLOR = 0x01-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
