# QueryMemberPurchaseEvent

```TypeScript
type QueryMemberPurchaseEvent = (memberPurchaseType: MemberPurchaseType) => Promise<MemberPurchaseInfo[]>
```

The query member purchase event.

@typedef { function } QueryMemberPurchaseEvent

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| memberPurchaseType | [MemberPurchaseType](arkts-avsession-avmusictemplate-memberpurchasetype-e.md) | Yes | [memberPurchaseType](arkts-avsession-avmusictemplate-memberpurchaseinfo-i.md) |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[MemberPurchaseInfo](arkts-avsession-avmusictemplate-memberpurchaseinfo-i.md)[]&gt; | (MemberPurchaseInfo[]) returned through promise |
