# PhotoCreateOptions (System API)

Defines the options for creating an image or video asset.

**Since:** 10

**Deprecated since:** 26.0.0

**Substitutes:** [PhotoCreateOptions](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photocreateoptions-i-sys.md)

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { userFileManager } from '@kit.CoreFileKit';
```

## cameraShotKey

```TypeScript
cameraShotKey?: string
```

Key for the Ultra Snapshot feature.

This parameter is available only for the system camera, and the key value is defined by the system camera.

**Type:** string

**Since:** 10

**Deprecated since:** 26.0.0

**Substitutes:** [cameraShotKey](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photocreateoptions-i-sys.md#camerashotkey)

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

## subType

```TypeScript
subType?: PhotoSubType
```

Subtype of the image or video.

**Type:** [PhotoSubType](arkts-corefile-userfilemanager-photosubtype-e-sys.md)

**Since:** 10

**Deprecated since:** 26.0.0

**Substitutes:** subType

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.
