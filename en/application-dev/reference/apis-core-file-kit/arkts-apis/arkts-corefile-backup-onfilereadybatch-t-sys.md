# OnFileReadyBatch (System API)

```TypeScript
type OnFileReadyBatch = (error: BusinessError<void>, files: Array<File>) => void
```

Function that returns array of file handle.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.StorageService.Backup

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| error | [BusinessError](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-businesserror-i.md)&lt;void&gt; | Yes | the error that triggers the callback. |
| files | Array&lt;[File](arkts-corefile-file-fs-file-i.md)&gt; | Yes | file handle. |
