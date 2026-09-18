# OnExecuteAIAction

```TypeScript
type OnExecuteAIAction = (id: string, params: string, result: OnAISessionCallback) => void
```

AI session execution operation callback function type. Used to implement custom AI model execution.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string | Yes | The session task ID. |
| params | string | Yes | Contextual data passed during execution (in JSON string format). |
| result | [OnAISessionCallback](arkts-arkweb-onaisessioncallback-t.md) | Yes | Callback function to notify the system of the execution result. |
