# MediaAssetProgressHandler

**MediaAssetProgressHandler** is used to obtain the media asset processing progress from **onProgress()**.

**Since:** 15

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## onProgress

```TypeScript
onProgress(progress: number): void
```

Called when the progress of the requested video is returned.

**Since:** 15

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| progress | number | Yes | Progress in percentage.<br>Value range: [0, 100] |
