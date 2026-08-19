# TextAreaSubmitCallback

```TypeScript
export type TextAreaSubmitCallback = (enterKeyType: EnterKeyType, event?: SubmitEvent) => void
```

Declare the event listener callback of the enter key.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type TextAreaSubmitCallback = (enterKeyType: EnterKeyType, event?: SubmitEvent) => void--><!--Device-unnamed-export type TextAreaSubmitCallback = (enterKeyType: EnterKeyType, event?: SubmitEvent) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enterKeyType | [EnterKeyType](arkts-arkui-textinput-enterkeytype-e.md) | 是 | The enter key type of soft keyboard. If the type is EnterKeyType.NEW_LINE, onSubmit is not triggered. |
| event | [SubmitEvent](arkts-arkui-textinput-submitevent-i.md) | 否 | Provides the method of keeping textArea editable state when submitted. |

