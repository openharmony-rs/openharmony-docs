# OnAISessionCallback

```TypeScript
type OnAISessionCallback = (state: AISessionResultType, content: string) => void
```

AI session operation result callback function type. Used to report the result of session creation or execution.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| state | [AISessionResultType](arkts-arkweb-aisessionresulttype-e.md) | Yes | The current result state. |
| content | string | Yes | The detailed result or response content. |
