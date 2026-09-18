# StyleOptions

Describes the style options.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## length

```TypeScript
length?: number
```

Length of the styled string style.

If the value is less than 0 or exceeds the difference between the string length and the value of **start**, it is treated as the difference between the string length and the value of **start**.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## start

```TypeScript
start?: number
```

Start position of the styled string style.

If the value is less than 0 or exceeds the string length, it is treated as **0**.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## styledValue

```TypeScript
styledValue: StyledStringValue
```

Style object.

**Type:** [StyledStringValue](arkts-arkui-styledstringvalue-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
