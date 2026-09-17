# CustomCommandEvent

```TypeScript
type CustomCommandEvent = (command: string, args: string) => Promise<OperResult>
```

The custom command event.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| command | string | Yes | request command. |
| args | string | Yes | arguments associated with event. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[OperResult](arkts-avsession-avmusictemplate-operresult-i.md)&gt; | Promise used to return OperResult. |
