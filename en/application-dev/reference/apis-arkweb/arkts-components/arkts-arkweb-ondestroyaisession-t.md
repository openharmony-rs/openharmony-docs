# OnDestroyAISession

```TypeScript
type OnDestroyAISession = (id: string) => void
```

AI session destruction callback function type. Used to clean up resources associated with the custom AI model.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string | Yes | The session task ID. |
