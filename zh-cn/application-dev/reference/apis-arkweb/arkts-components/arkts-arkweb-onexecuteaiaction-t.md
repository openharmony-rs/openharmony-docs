# OnExecuteAIAction

```TypeScript
type OnExecuteAIAction = (id: string, params: string, result: OnAISessionCallback) => void
```

AI会话执行操作回调函数类型。用于自定义实现AI模型执行。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 会话任务ID。 |
| params | string | 是 | 执行期间传递的上下文数据（以JSON字符串格式）。 |
| result | OnAISessionCallback | 是 | 通知执行结果的回调函数。 |

