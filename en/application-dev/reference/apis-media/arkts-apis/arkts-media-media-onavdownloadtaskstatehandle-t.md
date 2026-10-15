# OnAVDownloadTaskStateHandle

```TypeScript
type OnAVDownloadTaskStateHandle = (taskId: string, state: AVDownloadTaskState) => void
```

Registers a callback for the status change event of an offline download task.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-media-type OnAVDownloadTaskStateHandle = (taskId: string, state: AVDownloadTaskState) => void--><!--Device-media-type OnAVDownloadTaskStateHandle = (taskId: string, state: AVDownloadTaskState) => void-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| taskId | string | Yes | ID of the offline download task whose status changes. |
| state | [AVDownloadTaskState](arkts-media-media-avdownloadtaskstate-t.md) | Yes |  |
