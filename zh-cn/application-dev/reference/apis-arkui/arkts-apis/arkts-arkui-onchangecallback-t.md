# OnChangeCallback

```TypeScript
declare type OnChangeCallback = (value: boolean) => void
```

列表项右侧元素为Switch/CheckBox/Radio时，当状态发生改变时的回调函数对应的类型。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type OnChangeCallback = (value: boolean) => void--><!--Device-unnamed-declare type OnChangeCallback = (value: boolean) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 列表项右侧元素Switch/CheckBox/Radio选中状态改变时的回调函数。<br>value为true时，表示从未选中变为选中。<br>value为false时，表示从选中变为未选中。 |

