# OnRadioChangeCallback

```TypeScript
export type OnRadioChangeCallback = (isChecked: boolean) => void
```

单选框选中状态改变时触发的回调函数类型定义。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type OnRadioChangeCallback = (isChecked: boolean) => void--><!--Device-unnamed-export type OnRadioChangeCallback = (isChecked: boolean) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isChecked | boolean | 是 | 单选框的状态。\_\_\_HTML\_TAG\_USD\_0\_\_\_值为true时，表示从未选中变为选中。值为false时，表示从选中变为未选中。  |

