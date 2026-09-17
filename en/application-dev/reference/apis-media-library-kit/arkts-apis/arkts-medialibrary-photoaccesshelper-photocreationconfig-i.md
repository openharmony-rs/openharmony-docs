# PhotoCreationConfig

Represents the configuration for saving a media asset (image or video) to the media library, including the file name.

**Since:** 12

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## fileNameExtension

```TypeScript
fileNameExtension: string
```

File name extension, for example, **'jpg'**.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## photoType

```TypeScript
photoType: PhotoType
```

Type of the file to create, which can be **IMAGE** or **VIDEO**. See [PhotoType](arkts-medialibrary-photoaccesshelper-phototype-e.md).

**Type:** [PhotoType](arkts-medialibrary-photoaccesshelper-phototype-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## subtype

```TypeScript
subtype?: PhotoSubtype
```

Image or video file subtype. The default value is **DEFAULT**. See [PhotoSubtype](arkts-medialibrary-photoaccesshelper-photosubtype-e.md).

**Type:** [PhotoSubtype](arkts-medialibrary-photoaccesshelper-photosubtype-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## title

```TypeScript
title?: string
```

Title of the image or video. If this parameter is not passed, the system generates a title. The title must meet the following requirements:

- It must not contain a file name extension.  
- The total length of the file name, which is in the format of title+file name extension, must be between 1 and 2  
55 characters.  
- It must not contain any invalid characters, which are:\ / : * ? " ' ` &lt; &gt; | { } [ ]

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
