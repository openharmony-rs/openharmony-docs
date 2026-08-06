# OnUIPickerComponentCallback

```TypeScript
declare type OnUIPickerComponentCallback = (selectedIndex: number) => void
```

定义[onChange]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_和 [onScrollStop]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_事件的回调类型。

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type OnUIPickerComponentCallback = (selectedIndex: number) => void--><!--Device-unnamed-declare type OnUIPickerComponentCallback = (selectedIndex: number) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| selectedIndex | number | 是 | 当前选中项的索引值。 \_\_\_HTML\_TAG\_USD\_0\_\_\_取值范围：[0, 子组件的个数-1]内的整数。  |

