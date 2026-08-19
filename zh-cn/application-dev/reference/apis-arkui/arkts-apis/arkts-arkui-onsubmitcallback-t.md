# OnSubmitCallback

```TypeScript
export type OnSubmitCallback = (enterKey: EnterKeyType, event: SubmitEvent) => void
```

提交回调。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type OnSubmitCallback = (enterKey: EnterKeyType, event: SubmitEvent) => void--><!--Device-unnamed-export type OnSubmitCallback = (enterKey: EnterKeyType, event: SubmitEvent) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enterKey | [EnterKeyType](arkts-arkui-textinput-enterkeytype-e.md) | 是 | 输入法回车键类型。 |
| event | [SubmitEvent](arkts-arkui-textinput-submitevent-i.md) | 是 | 提交事件。可以控制是否收起键盘。 |

