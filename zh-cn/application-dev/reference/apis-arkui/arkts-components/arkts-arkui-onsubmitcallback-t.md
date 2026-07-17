# OnSubmitCallback

```TypeScript
declare type OnSubmitCallback = (enterKey: EnterKeyType, event: SubmitEvent) => void
```

提交回调。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type OnSubmitCallback = (enterKey: EnterKeyType, event: SubmitEvent) => void--><!--Device-unnamed-declare type OnSubmitCallback = (enterKey: EnterKeyType, event: SubmitEvent) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enterKey | EnterKeyType | 是 | 输入法回车键类型。 |
| event | SubmitEvent | 是 | 提交事件。可以控制是否收起键盘。 |

