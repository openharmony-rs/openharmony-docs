# OnAISessionCallback

```TypeScript
export type OnAISessionCallback = (state: AISessionResultType, content: string) => void
```

Callback type for AI session operations. Used to report the result of session creation or execution.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type OnAISessionCallback = (state: AISessionResultType, content: string) => void--><!--Device-unnamed-export type OnAISessionCallback = (state: AISessionResultType, content: string) => void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| state | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | The current result state.  |
| content | string | 是 | The detailed result or response content.  |

