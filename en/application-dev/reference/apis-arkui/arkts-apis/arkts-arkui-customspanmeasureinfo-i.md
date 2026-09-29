# CustomSpanMeasureInfo

```TypeScript
declare interface CustomSpanMeasureInfo
```

Defines the CustomSpanMeasureInfo interface.

**Since:** 12

<!--Device-unnamed-declare interface CustomSpanMeasureInfo--><!--Device-unnamed-declare interface CustomSpanMeasureInfo-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize: number
```

Font size of the text.

Unit: [fp](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#basic-pixel-units)

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-CustomSpanMeasureInfo-fontSize: number--><!--Device-CustomSpanMeasureInfo-fontSize: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## layoutPolicy

```TypeScript
layoutPolicy?: LayoutPolicy
```

Width layout policy of the parent component where the custom drawing span is located.

**NOTE:** 

When the value is **null** or **undefined**, it indicates that the parent component has no width layout policy set.

**Type:** [LayoutPolicy](../arkts-components/arkts-arkui-common-comp-layoutpolicy-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-CustomSpanMeasureInfo-layoutPolicy?: LayoutPolicy--><!--Device-CustomSpanMeasureInfo-layoutPolicy?: LayoutPolicy-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## maxWidth

```TypeScript
maxWidth?: number
```

Maximum width constraint of the content area of the parent component where the custom drawing span is located.

Default value: uses its own width.

Unit: [px](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#basic-pixel-units)

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-CustomSpanMeasureInfo-maxWidth?: number--><!--Device-CustomSpanMeasureInfo-maxWidth?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
