# OnExecuteAIAction

```TypeScript
export type OnExecuteAIAction = (id: string, params: string, result: OnAISessionCallback) => void
```

Triggered when executing an AI session action. Enables custom implementation of AI model execution.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type OnExecuteAIAction = (id: string, params: string, result: OnAISessionCallback) => void--><!--Device-unnamed-export type OnExecuteAIAction = (id: string, params: string, result: OnAISessionCallback) => void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | The session task ID. |
| params | string | 是 | Contextual data passed during execution (in JSON string format). |
| result | [OnAISessionCallback](arkts-na-onaisessioncallback-t.md) | 是 | Callback function to notify the system of the execution result. |

