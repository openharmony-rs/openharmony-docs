# SubmitCallback

```TypeScript
declare type SubmitCallback = (enterKey: EnterKeyType, event: SubmitEvent) => void
```

软键盘按下回车键时的回调事件。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enterKey | EnterKeyType | 是 | 软键盘输入法回车键类型。具体类型见EnterKeyType枚举说明。 |
| event | SubmitEvent | 是 | 当提交的时候，提供保持组件编辑状态的方法。EnterKeyType指定为NEW_LINE时，默认保持编辑态。 |

