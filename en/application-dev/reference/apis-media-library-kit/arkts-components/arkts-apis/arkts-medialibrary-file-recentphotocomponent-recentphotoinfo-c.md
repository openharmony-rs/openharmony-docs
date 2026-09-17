# RecentPhotoInfo

Represents information about the recent image or video.

**Since:** 13

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { RecentPhotoComponent, RecentPhotoCheckResultCallback, RecentPhotoInfo, RecentPhotoCheckInfoCallback, RecentPhotoClickCallback, RecentPhotoOptions, PhotoSource } from '@kit.MediaLibraryKit';
```

## dateTaken

```TypeScript
dateTaken?: number
```

Time when the recent image or video is taken, in ms. The value is the number of milliseconds elapsed since the Unix epoch (00:00:00 UTC on January 1, 1970).

**Type:** number

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## identifier

```TypeScript
identifier?: string
```

Hash value of the name of the recent image or video, which is used to help the application determine whether the image or video to be displayed is the same as the one displayed before.

**Type:** string

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
