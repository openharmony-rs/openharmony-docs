# CreationSetting

Represents the configuration for saving images or videos to the media library, including the file name, file type, and other related parameters.

**Since:** 23

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

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## photoType

```TypeScript
photoType: PhotoType
```

[PhotoType](arkts-medialibrary-photoaccesshelper-phototype-e.md) of the created media file, which can be **IMAGE** or **VIDEO**.

**Type:** [PhotoType](arkts-medialibrary-photoaccesshelper-phototype-e.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## title

```TypeScript
title?: string
```

Title of the image or video.

If this parameter is not passed, the system generates a value. The parameter specifications are as follows:

- It must not contain a file name extension.  
- It must not contain any invalid characters, which are:\ / : * ? " ' ` &lt; &gt; | { } [ ]  
- The file name consists of the title and file name extension. The file name string length ranges from 1 to 255.  
Therefore, the title length cannot be too long.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
