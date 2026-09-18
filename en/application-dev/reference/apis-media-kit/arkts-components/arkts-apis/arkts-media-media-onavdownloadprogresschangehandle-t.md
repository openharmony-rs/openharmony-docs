# OnAVDownloadProgressChangeHandle

```TypeScript
type OnAVDownloadProgressChangeHandle = (taskId: string, progress: number) => void
```

Describes the callback invoked for the AVDownloader progress change event.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Media.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| taskId | string | Yes | ID of the task whose status changes. |
| progress | number | Yes |  |
