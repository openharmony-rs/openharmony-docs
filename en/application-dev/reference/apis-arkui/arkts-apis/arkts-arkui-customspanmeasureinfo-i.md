# CustomSpanMeasureInfo

Defines the CustomSpanMeasureInfo interface.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize: number
```

Text font size.

Unit: fp

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## layoutPolicy

```TypeScript
layoutPolicy?: LayoutPolicy
```

Width layout policy of the parent component of the custom span.

**NOTE:** 

When the value is **null** or **undefined**, the parent component does not have a width layout policy set.

**Type:** [LayoutPolicy](../arkts-components/arkts-arkui-layoutpolicy-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## maxWidth

```TypeScript
maxWidth?: number
```

Maximum width constraint of the custom span within the parent component's content area.

Unit: px

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
