# DecorationStyle

```TypeScript
declare class DecorationStyle
```

Describes the text decorative line style.

**Since:** 12

<!--Device-unnamed-declare class DecorationStyle--><!--Device-unnamed-declare class DecorationStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(value: DecorationStyleInterface)
```

A constructor used to create a text decoration line style. If this API is not used to set the style, the default decoration line type is **TextDecorationType.None**, the color is **Color.Black**, and the style is **TextDecorationStyle.SOLID**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DecorationStyle-constructor(value: DecorationStyleInterface)--><!--Device-DecorationStyle-constructor(value: DecorationStyleInterface)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [DecorationStyleInterface](arkts-arkui-decorationstyleinterface-i.md) | Yes | Text decoration settings. |

<a id="constructor-1"></a>

## constructor

```TypeScript
constructor(value: DecorationStyleInterface, options?: DecorationOptions)
```

A constructor used to create a text decoration line style, with additional configuration options. If this API is not used to set the style, the default decoration line type is **TextDecorationType.None**, the color is **Color.Black**, the style is **TextDecorationStyle.SOLID**, and the thickness scale is 1.0.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-DecorationStyle-constructor(value: DecorationStyleInterface, options?: DecorationOptions)--><!--Device-DecorationStyle-constructor(value: DecorationStyleInterface, options?: DecorationOptions)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [DecorationStyleInterface](arkts-arkui-decorationstyleinterface-i.md) | Yes | Text decoration line settings. |
| options | [DecorationOptions](arkts-arkui-decorationoptions-i.md) | No | Additional configuration options for the text decoration line. |

## color

```TypeScript
readonly color?: ResourceColor
```

Color of the text decoration line of the styled string.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DecorationStyle-readonly color?: ResourceColor--><!--Device-DecorationStyle-readonly color?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## options

```TypeScript
readonly options?: DecorationOptions
```

Additional configuration options of the text decoration line style of the styled string.

**Type:** [DecorationOptions](arkts-arkui-decorationoptions-i.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-DecorationStyle-readonly options?: DecorationOptions--><!--Device-DecorationStyle-readonly options?: DecorationOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## style

```TypeScript
readonly style?: TextDecorationStyle
```

Style of the text decoration line of the styled string.

**Type:** [TextDecorationStyle](arkts-arkui-textdecorationstyle-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DecorationStyle-readonly style?: TextDecorationStyle--><!--Device-DecorationStyle-readonly style?: TextDecorationStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## thicknessScale

```TypeScript
readonly thicknessScale?: number
```

Scale value of the text decoration line thickness of the styled string.

**Type:** number

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-DecorationStyle-readonly thicknessScale?: number--><!--Device-DecorationStyle-readonly thicknessScale?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
readonly type: TextDecorationType
```

Type of the text decoration line of the styled string.

**Type:** [TextDecorationType](arkts-arkui-textdecorationtype-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DecorationStyle-readonly type: TextDecorationType--><!--Device-DecorationStyle-readonly type: TextDecorationType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
