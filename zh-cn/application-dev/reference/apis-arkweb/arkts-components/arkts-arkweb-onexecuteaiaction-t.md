# OnExecuteAIAction

```TypeScript
type OnExecuteAIAction = (id: string, params: string, result: OnAISessionCallback) => void
```

AI会话执行操作回调函数类型。用于自定义实现AI模型执行。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-type OnExecuteAIAction = (id: string, params: string, result: OnAISessionCallback) => void--><!--Device-unnamed-type OnExecuteAIAction = (id: string, params: string, result: OnAISessionCallback) => void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | The session task ID. |
| params | string | 是 | Contextual data passed during execution (in JSON string format). |
| result | [OnAISessionCallback](arkts-arkweb-onaisessioncallback-t.md) | 是 | Callback function to notify the system of the execution result. |

