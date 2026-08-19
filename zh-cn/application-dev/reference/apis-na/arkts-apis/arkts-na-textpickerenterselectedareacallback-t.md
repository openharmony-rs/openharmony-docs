# TextPickerEnterSelectedAreaCallback

```TypeScript
export type TextPickerEnterSelectedAreaCallback = (value: string | string[], index: int | int[]) => void
```

定义触发onEnterSelectedArea事件的回调类型。 在多列联动场景中，不建议使用该回调，由于该回调标识的是滑动过程中选项进入分割线区域内的节点，而跟随变化的选项并不涉及滑动，因此， 回调的返回值中，仅当前滑动列的值会正常变化，其余未滑动列的值保持不变。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type TextPickerEnterSelectedAreaCallback = (value: string | string[], index: int | int[]) => void--><!--Device-unnamed-export type TextPickerEnterSelectedAreaCallback = (value: string | string[], index: int | int[]) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string \| string[] | 是 | 当前选中项的文本。多列数据选择器的value为数组类型。<br/>**说明：**<br/>当选择器内容为 文本或图文混排时，value值为选中项中的文本值；当选择器内容为图片时，value值为空。 |
| index | int \| int[] | 是 | 当前选中项的索引值，索引从0开始。多列数据选择器的index为数组类型。 |

