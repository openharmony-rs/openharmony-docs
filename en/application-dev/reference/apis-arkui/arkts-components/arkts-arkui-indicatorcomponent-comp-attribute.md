# IndicatorComponent properties/events

Defines the IndicatorComponent attribute functions.

@extends CommonMethod&lt;IndicatorComponentAttribute&gt;

**Inheritance/Implementation:** IndicatorComponentAttribute extends CommonMethod<IndicatorComponentAttribute>

**Since:** 15

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## count

```TypeScript
count(totalCount: number)
```

Sets the total number of indicator.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**Widget capability:** This API can be used in ArkTS widgets since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| totalCount | number | Yes |  |

## initialIndex

```TypeScript
initialIndex(index: number)
```

Called when the index value of the displayed subcomponent is set in the container.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**Widget capability:** This API can be used in ArkTS widgets since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes |  |

## loop

```TypeScript
loop(isLoop: boolean)
```

Called when setting whether to turn on cyclic sliding.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**Widget capability:** This API can be used in ArkTS widgets since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isLoop | boolean | Yes |  |

## onChange

```TypeScript
onChange(event: Callback<number>)
```

Called when the index value changes.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**Widget capability:** This API can be used in ArkTS widgets since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | Callback&lt;number&gt; | Yes |  |

## style

```TypeScript
style(indicatorStyle: DotIndicator | DigitIndicator)
```

Sets the indicator style.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**Widget capability:** This API can be used in ArkTS widgets since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| indicatorStyle | [DotIndicator](arkts-arkui-dotindicator-c.md) &#124; [DigitIndicator](arkts-arkui-digitindicator-c.md) | Yes | the style value |

## vertical

```TypeScript
vertical(isVertical: boolean)
```

Called when setting whether to slide vertically.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**Widget capability:** This API can be used in ArkTS widgets since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isVertical | boolean | Yes |  |
