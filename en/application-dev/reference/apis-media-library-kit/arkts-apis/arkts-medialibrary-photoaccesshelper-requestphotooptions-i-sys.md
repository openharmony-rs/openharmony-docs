# RequestPhotoOptions (System API)

```TypeScript
interface RequestPhotoOptions
```

Defines the options for obtaining the thumbnail of an image or video.

**Since:** 11

<!--Device-photoAccessHelper-interface RequestPhotoOptions--><!--Device-photoAccessHelper-interface RequestPhotoOptions-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## requestPhotoType

```TypeScript
requestPhotoType?: RequestPhotoType
```

Operation to perform.

**Type:** [RequestPhotoType](arkts-medialibrary-photoaccesshelper-requestphototype-e-sys.md)

**Since:** 11

<!--Device-RequestPhotoOptions-requestPhotoType?: RequestPhotoType--><!--Device-RequestPhotoOptions-requestPhotoType?: RequestPhotoType-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## size

```TypeScript
size?: image.Size
```

Size of the thumbnail to obtain.

**Type:** [image.Size](../../apis-image-kit/arkts-apis/arkts-image-image-size-i.md)

**Since:** 11

<!--Device-RequestPhotoOptions-size?: image.Size--><!--Device-RequestPhotoOptions-size?: image.Size-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.
