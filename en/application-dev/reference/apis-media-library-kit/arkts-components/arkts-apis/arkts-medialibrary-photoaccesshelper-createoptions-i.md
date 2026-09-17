# CreateOptions

Options for creating an image or video asset.

The title must meet the following requirements:

- It must not contain a file name extension.  
- The total length of the file name must be between 1 and 255 characters.

**Since:** 10

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## subtype

```TypeScript
subtype?: PhotoSubtype
```

Subtype of the image or video file.

**Type:** [PhotoSubtype](arkts-medialibrary-photoaccesshelper-photosubtype-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## title

```TypeScript
title?: string
```

Title of the image or video.

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
