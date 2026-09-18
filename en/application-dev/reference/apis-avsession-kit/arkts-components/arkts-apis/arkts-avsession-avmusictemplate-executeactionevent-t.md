# ExecuteActionEvent

```TypeScript
type ExecuteActionEvent = (actionType: string, params: string) => Promise<string>
```

The execute action event.

@typedef { function } ExecuteActionEvent

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| actionType | string | Yes | action type |
| params | string | Yes | params |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | (string) returned through promise |
