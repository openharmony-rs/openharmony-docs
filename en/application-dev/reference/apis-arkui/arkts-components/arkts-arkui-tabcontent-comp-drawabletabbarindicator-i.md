# DrawableTabBarIndicator

```TypeScript
declare interface DrawableTabBarIndicator
```

Uses an image resource as the indicator.

**Since:** 22

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderRadius

```TypeScript
borderRadius?: Length
```

Rounded corner radius of the indicator. It cannot be set in percentage.

Default value: **0.0**

Unit: vp

Value range: [0, +∞)

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Default:** 0

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## drawable

```TypeScript
drawable?: DrawableDescriptor
```

Image resource of the indicator. Supported types: [DrawableDescriptor](../arkts-apis/arkts-arkui-arkui-drawabledescriptor-drawabledescriptorloadedresult-i.md), [PixelMapDrawableDescriptor](../arkts-apis/arkts-arkui-arkui-drawabledescriptor-pixelmapdrawabledescriptor-c.md), [LayeredDrawableDescriptor](../arkts-apis/arkts-arkui-arkui-drawabledescriptor-layereddrawabledescriptor-c.md), and [AnimatedDrawableDescriptor](../arkts-apis/arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md). If an invalid image resource is passed, the default solid indicator is displayed.

**Type:** [DrawableDescriptor](arkts-arkui-tabcontent-comp-drawabledescriptor-t.md)

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## height

```TypeScript
height?: Length
```

Height of the indicator. It cannot be set in percentage.

Default value: **2.0**

Unit: vp

Value range: [0, +∞)

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Default:** 2vp

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## marginTop

```TypeScript
marginTop?: Length
```

Spacing between the indicator and text. It cannot be set in percentage.

Default value: **8.0**

Unit: vp

Value range: [0, +∞)

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Default:** 8vp

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: Length
```

Width of the indicator. It cannot be set in percentage.

Default value: **0.0**

Unit: vp

Value range: [0, +∞)

If this parameter is set to **0**, the tab text width will be used instead.

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Default:** 0

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
