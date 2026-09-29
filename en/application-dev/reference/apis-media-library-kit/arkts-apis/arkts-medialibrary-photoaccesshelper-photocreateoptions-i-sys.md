# PhotoCreateOptions (System API)

```TypeScript
interface PhotoCreateOptions
```

Options for creating an image or video asset.

**Since:** 10

<!--Device-photoAccessHelper-interface PhotoCreateOptions--><!--Device-photoAccessHelper-interface PhotoCreateOptions-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## cameraShotKey

```TypeScript
cameraShotKey?: string
```

Key for the Ultra Snapshot feature, which allows the camera to take photos or record videos with the screen off. (This parameter is available only for the system camera, and the key value is defined by the system camera.)

**Type:** string

**Since:** 10

<!--Device-PhotoCreateOptions-cameraShotKey?: string--><!--Device-PhotoCreateOptions-cameraShotKey?: string-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## subtype

```TypeScript
subtype?: PhotoSubtype
```

Subtype of the image or video.

**Type:** [PhotoSubtype](arkts-medialibrary-photoaccesshelper-photosubtype-e.md)

**Since:** 10

<!--Device-PhotoCreateOptions-subtype?: PhotoSubtype--><!--Device-PhotoCreateOptions-subtype?: PhotoSubtype-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## userId

```TypeScript
userId?: number
```

User ID.

**Type:** number

**Since:** 19

<!--Device-PhotoCreateOptions-userId?: int--><!--Device-PhotoCreateOptions-userId?: int-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.
