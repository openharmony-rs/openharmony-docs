# RequestDialogInfoEvent

```TypeScript
type RequestDialogInfoEvent = (actionType: DialogActionType, actionInfo?: DialogActionInfo) => Promise<DialogInfo>
```

The request dialog info event.

@typedef { function } RequestDialogInfoEvent

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| actionType | [DialogActionType](arkts-avsession-avmusictemplate-dialogactiontype-t.md) | Yes | action type |
| actionInfo | [DialogActionInfo](arkts-avsession-avmusictemplate-dialogactioninfo-i.md) | No | action info |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[DialogInfo](arkts-avsession-avmusictemplate-dialoginfo-i.md)&gt; | (DialogInfo) returned through promise |
