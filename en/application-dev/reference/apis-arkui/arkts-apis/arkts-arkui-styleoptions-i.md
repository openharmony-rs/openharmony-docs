# StyleOptions

```TypeScript
declare interface StyleOptions
```

Describes the style options.

**Since:** 12

<!--Device-unnamed-declare interface StyleOptions--><!--Device-unnamed-declare interface StyleOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## length

```TypeScript
length?: number
```

Length for setting the style of the styled string.

If the value of **length** is less than 0 or exceeds the difference between the string length and **start**, it is processed as the difference between the string length and **start**.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-StyleOptions-length?: number--><!--Device-StyleOptions-length?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## start

```TypeScript
start?: number
```

Start position for setting the style of the styled string.

If the value of **start** is less than 0 or exceeds the string length, it is processed as 0.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-StyleOptions-start?: number--><!--Device-StyleOptions-start?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## styledKey

```TypeScript
styledKey: StyledStringKey
```

Style key.

**Type:** [StyledStringKey](arkts-arkui-styledstringkey-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-StyleOptions-styledKey: StyledStringKey--><!--Device-StyleOptions-styledKey: StyledStringKey-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## styledValue

```TypeScript
styledValue: StyledStringValue
```

Style object used to set the style of the styled string.

**Type:** [StyledStringValue](arkts-arkui-styledstringvalue-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-StyleOptions-styledValue: StyledStringValue--><!--Device-StyleOptions-styledValue: StyledStringValue-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
