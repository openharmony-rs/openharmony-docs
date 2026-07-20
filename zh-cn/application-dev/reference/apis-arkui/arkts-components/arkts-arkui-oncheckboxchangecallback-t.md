# OnCheckboxChangeCallback

```TypeScript
declare type OnCheckboxChangeCallback = (value: boolean) => void
```

选中的状态。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-unnamed-declare type OnCheckboxChangeCallback = (value: boolean) => void--><!--Device-unnamed-declare type OnCheckboxChangeCallback = (value: boolean) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 返回true表示已选中。返回false表示未选中。  |

