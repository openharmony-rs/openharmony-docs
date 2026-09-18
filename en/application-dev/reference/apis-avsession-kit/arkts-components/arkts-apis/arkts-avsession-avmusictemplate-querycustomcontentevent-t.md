# QueryCustomContentEvent

```TypeScript
type QueryCustomContentEvent = (queryType: CustomType[]) => Promise<CustomElement>
```

The query custom content event.

@typedef { function } QueryCustomContentEvent

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| queryType | [CustomType](arkts-avsession-avmusictemplate-customtype-t.md)[] | Yes | query type |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[CustomElement](arkts-avsession-avmusictemplate-customelement-i.md)&gt; | (CustomElement) returned through promise |
