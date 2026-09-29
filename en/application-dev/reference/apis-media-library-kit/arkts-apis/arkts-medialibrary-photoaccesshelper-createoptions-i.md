# CreateOptions

```TypeScript
interface CreateOptions
```

Options for creating an image or video asset.

The title must meet the following requirements:

- It must not contain a file name extension.  
- The total length of the file name must be between 1 and 255 characters.

**Since:** 10

<!--Device-photoAccessHelper-interface CreateOptions--><!--Device-photoAccessHelper-interface CreateOptions-End-->

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

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-CreateOptions-subtype?: PhotoSubtype--><!--Device-CreateOptions-subtype?: PhotoSubtype-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## title

```TypeScript
title?: string
```

Title of the image or video.

**Type:** string

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-CreateOptions-title?: string--><!--Device-CreateOptions-title?: string-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
