# PhotoSelectOptions

```TypeScript
class PhotoSelectOptions
```

Defines the options for selecting images or videos.

**Since:** 9

**Deprecated since:** 12

**Substitutes:** [PhotoSelectOptions](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoselectoptions-c.md)

**System capability:** SystemCapability.FileManagement.UserFileService

## Modules to Import

```TypeScript
import { picker } from '@kit.CoreFileKit';
```

## maxSelectNumber

```TypeScript
maxSelectNumber?: number
```

Maximum number of media files that can be selected. The default value is **50**, and the maximum value is **500**.

**Type:** number

**Since:** 9

**Deprecated since:** 18

**Substitutes:** maxSelectNumber

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.FileManagement.UserFileService

## MIMEType

```TypeScript
MIMEType?: PhotoViewMIMETypes
```

Media file types to select. If this parameter is not specified, **IMAGE_VIDEO_TYPE** is used by default.

**Note:**  This API is supported since API version 9 and deprecated since API version 18.

**Type:** [PhotoViewMIMETypes](arkts-corefile-picker-photoviewmimetypes-e.md)

**Since:** 9

**Deprecated since:** 18

**Substitutes:** MIMEType

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.FileManagement.UserFileService
