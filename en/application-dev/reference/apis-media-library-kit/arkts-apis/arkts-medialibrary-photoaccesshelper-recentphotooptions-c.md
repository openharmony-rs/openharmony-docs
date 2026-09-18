# RecentPhotoOptions

RecentPhotoOptions Object

**Since:** 20

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## MIMEType

```TypeScript
MIMEType?: photoAccessHelper.PhotoViewMIMETypes
```

Types of the file displayed. The default value is **PhotoViewMIMETypes.IMAGE_VIDEO_TYPE**.

**Type:** [photoAccessHelper.PhotoViewMIMETypes](arkts-medialibrary-photoaccesshelper-photoviewmimetypes-e.md)

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## period

```TypeScript
period?: number
```

Time range for displaying the recent images or videos, measured in seconds. After setting, the system shows images or videos taken within the specified time from the current moment. The longest duration you can set is 1 day (86400s).

If the value is less than or equal to 0, greater than 86400, or not set, the system uses the longest duration (1 day) by default. If there are no images or videos within the set time range, the component does not show anything.

**Type:** number

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## photoSource

```TypeScript
photoSource?: PhotoSource
```

Source of the recent image or video, for example, image or video taken by the camera or screenshot. By default, the source is not restricted.

**Type:** [PhotoSource](arkts-medialibrary-photoaccesshelper-photosource-e.md)

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
