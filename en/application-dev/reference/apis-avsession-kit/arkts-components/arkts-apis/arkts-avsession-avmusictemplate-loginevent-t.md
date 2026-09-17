# LoginEvent

```TypeScript
type LoginEvent = (controlType: LoginType, id?: string) => Promise<QrCodeInfo[]>
```

The login event.

@typedef { function } LoginEvent

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| controlType | [LoginType](arkts-avsession-avmusictemplate-logintype-t.md) | Yes | control type |
| id | string | No | id |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[QrCodeInfo](arkts-avsession-avmusictemplate-qrcodeinfo-i.md)[]&gt; | (QrCodeInfo[]) returned through promise |
