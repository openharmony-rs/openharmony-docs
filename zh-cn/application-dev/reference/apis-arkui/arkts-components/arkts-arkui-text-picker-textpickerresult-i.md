# TextPickerResult

文本选择器结果。

**起始版本：** 8

<!--Device-unnamed-declare interface TextPickerResult--><!--Device-unnamed-declare interface TextPickerResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## index

```TypeScript
index: number | number[]
```

选中项在选择范围数组中的索引值，索引从0开始。（文本选择器显示多列时，index为数组类型。）

**类型：** number | number[]

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerResult-index: number | number[]--><!--Device-TextPickerResult-index: number | number[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: string | string[]
```

选中项的文本内容。

**说明**：当显示文本或图片加文本列表时，value值为选中项中的文本值。（文本选择器显示多列时，value为数组类型。）

当显示图片列表时，value值为空。

value值不支持包含转义字符'\'。

**类型：** string | string[]

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextPickerResult-value: string | string[]--><!--Device-TextPickerResult-value: string | string[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

