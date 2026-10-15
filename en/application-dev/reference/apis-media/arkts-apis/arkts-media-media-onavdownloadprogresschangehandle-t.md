# OnAVDownloadProgressChangeHandle

```TypeScript
type OnAVDownloadProgressChangeHandle = (taskId: string, progress: number) => void
```

Registers a callback for the progress change event of an offline download task. This event is triggered when the download progress changes by more than 1% compared to the last time and the interval since the last triggering exceeds 500 ms.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-media-type OnAVDownloadProgressChangeHandle = (taskId: string, progress: double) => void--><!--Device-media-type OnAVDownloadProgressChangeHandle = (taskId: string, progress: double) => void-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| taskId | string | Yes | ID of an offline download task. |
| progress | number | Yes |  |
