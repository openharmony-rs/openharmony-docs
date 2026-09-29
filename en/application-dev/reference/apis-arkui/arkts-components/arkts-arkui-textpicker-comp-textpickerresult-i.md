# TextPickerResult

```TypeScript
declare interface TextPickerResult
```

Represents the selection result of a **TextPicker** component.

**Since:** 8

<!--Device-unnamed-declare interface TextPickerResult--><!--Device-unnamed-declare interface TextPickerResult-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## index

```TypeScript
index: number[]
```

Index of the selected item in the range. The index is zero-based. (For a multi-column picker, **index** is of the array type.)

**Type:** number[]

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextPickerResult-index: number | number[]--><!--Device-TextPickerResult-index: number | number[]-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: string[]
```

Text of the selected item.

**NOTE:** 

When the picker contains text only or both text and imagery, **value** indicates the text value of the selected item. (For a multi-column picker, **value** is of the array type.)

For an image list, **value** is empty.

The value must be within the range defined by the **range** attribute and cannot contain the escape character ().

**Type:** string[]

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextPickerResult-value: string | string[]--><!--Device-TextPickerResult-value: string | string[]-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
