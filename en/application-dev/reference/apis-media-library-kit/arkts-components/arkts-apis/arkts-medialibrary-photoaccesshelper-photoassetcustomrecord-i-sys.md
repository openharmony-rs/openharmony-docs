# PhotoAssetCustomRecord (System API)

Provides APIs for custom user behavior recording for Gallery.

**Since:** 20

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## fileId

```TypeScript
readonly fileId: number
```

File ID, which must be an integer greater than 0.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## lcdJumpCount

```TypeScript
readonly lcdJumpCount: number
```

Number of times the image or video was jumped to in large view. The value must be an integer greater than 0.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## shareCount

```TypeScript
readonly shareCount: number
```

Number of times that image or video was shared. The value must be an integer greater than 0.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.
