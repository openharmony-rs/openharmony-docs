# OnAISessionCallback

```TypeScript
type OnAISessionCallback = (state: AISessionResultType, content: string) => void
```

AI会话操作结果回调函数类型。用于报告会话创建或执行的结果。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| state | AISessionResultType | 是 | The current result state. |
| content | string | 是 | The detailed result or response content. |

