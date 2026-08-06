# OnUIPickerComponentCallback

```TypeScript
export declare type OnUIPickerComponentCallback = (selectedIndex: int) => void
```

定义[onChange]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_和[onScrollStop]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_事件的回调类型。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare type OnUIPickerComponentCallback = (selectedIndex: int) => void--><!--Device-unnamed-export declare type OnUIPickerComponentCallback = (selectedIndex: int) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| selectedIndex | int | 是 | 当前选中项的索引值。\_\_\_HTML\_TAG\_USD\_0\_\_\_取值范围：[0, 子组件的个数-1]内的整数。  |

