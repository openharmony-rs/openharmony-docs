# HandleMemberPurchaseEvent

```TypeScript
type HandleMemberPurchaseEvent = (info: MemberPurchaseInfo) => Promise<DialogInfo>
```

The handle member purchase event.

@typedef { function } HandleMemberPurchaseEvent

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [MemberPurchaseInfo](arkts-avsession-avmusictemplate-memberpurchaseinfo-i.md) | Yes | info |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[DialogInfo](arkts-avsession-avmusictemplate-dialoginfo-i.md)&gt; | (DialogInfo) returned through promise |
