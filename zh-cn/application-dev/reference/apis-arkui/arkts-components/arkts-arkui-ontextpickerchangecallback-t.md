# OnTextPickerChangeCallback

```TypeScript
declare type OnTextPickerChangeCallback = (selectItem: string | string[], index: number | number[]) => void
```

定义触发onChange事件的回调类型。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| selectItem | string \| string[] | 是 | 当前选中项的文本。多列数据选择器的selectItem为数组类型。**说明：**当选择器内容为文本或图文混排时，selectItem值为选中项中的文本值；当选择器内容为图片时，selectItem值为空。 |
| index | number \| number[] | 是 | 当前选中项的索引值，索引从0开始。多列数据选择器的index为数组类型。 |

