# TextPickerResult

```TypeScript
declare interface TextPickerResult
```

Defines the struct of TextPickerResult.

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## index

```TypeScript
index: number[]
```

The subscript of the current selection.

**Type:** number[]

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: string[]
```

The currently selected value. Only valid when only text is displayed.When picture or picture plus text is displayed, the value of value is "".

**Type:** string[]

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
