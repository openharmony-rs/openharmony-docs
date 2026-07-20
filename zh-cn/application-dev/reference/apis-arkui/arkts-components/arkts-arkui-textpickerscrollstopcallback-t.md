# TextPickerScrollStopCallback

```TypeScript
declare type TextPickerScrollStopCallback = (value: string | string[], index: number | number[]) => void
```

定义触发onScrollStop事件的回调类型。

**说明：**

- 当选择器内容为文本或图文混排时，value值为选中项中的文本值；  
- 当选择器内容为图片时，value值为空。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type TextPickerScrollStopCallback = (value: string | string[], index: number | number[]) => void--><!--Device-unnamed-declare type TextPickerScrollStopCallback = (value: string | string[], index: number | number[]) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string \| string[] | 是 | 当前选中项的文本。多列数据选择器的value为数组类型。  |
| index | number \| number[] | 是 | 当前选中项的索引值，索引从0开始。多列数据选择器的index为数组类型。  |

