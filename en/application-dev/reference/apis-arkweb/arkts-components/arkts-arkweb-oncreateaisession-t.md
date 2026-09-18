# OnCreateAISession

```TypeScript
type OnCreateAISession = (id: string, params: string, result: OnAISessionCallback) => boolean
```

AI session creation callback function type. Allows custom model initialization and result processing.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string | Yes | The session task ID. |
| params | string | Yes | Contextual data passed during creation. |
| result | [OnAISessionCallback](arkts-arkweb-onaisessioncallback-t.md) | Yes | Callback function to notify the system of the creation result. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | The value **true** indicates that custom logic is used, skipping the system default behavior; **false** indicates that the system default logic continues to be executed. |
