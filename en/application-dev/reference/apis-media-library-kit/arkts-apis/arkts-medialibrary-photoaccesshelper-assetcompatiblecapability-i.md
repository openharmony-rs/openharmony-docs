# AssetCompatibleCapability

Defines the asset compatibility capability.

**Since:** 24

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## supportedHighResolution

```TypeScript
supportedHighResolution: boolean
```

Whether high-resolution assets are supported. **true**: yes; **false**: no.

**Type:** boolean

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## supportedMimeType

```TypeScript
supportedMimeType?: Array<string>
```

Supported MIME types.

**Type:** Array&lt;string&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
