# RecommendationOptions

Defines the image recommendation options. The image recommendation feature depends on the image data analysis capability, which varies with devices.

**Since:** 11

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## recommendationType

```TypeScript
recommendationType?: RecommendationType
```

Type of the recommended image.

**Type:** [RecommendationType](arkts-medialibrary-photoaccesshelper-recommendationtype-e.md)

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## textContextInfo

```TypeScript
textContextInfo?: TextContextInfo
```

Text based on which images are recommended. If both **recommendationType** and **textContextInfo** are set, **textContextInfo** takes precedence over **recommendationType**.

**Type:** [TextContextInfo](arkts-medialibrary-photoaccesshelper-textcontextinfo-i.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
