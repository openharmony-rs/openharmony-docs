# ProgressListener (System API)

```TypeScript
type ProgressListener = (progress: Progress) => void
```

Indicates the type of the progress of batch operation.

Progress callback, which can be the size or numberof files.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| progress | [Progress](arkts-medialibrary-photoaccesshelper-progress-i-sys.md) | Yes | progress info. |
