# RecommendationOptions

```TypeScript
class RecommendationOptions
```

Defines the image recommendation options. The image recommendation feature depends on the image data analysis capability, which varies with devices.

**Since:** 11

<!--Device-photoAccessHelper-class RecommendationOptions--><!--Device-photoAccessHelper-class RecommendationOptions-End-->

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

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-RecommendationOptions-recommendationType?: RecommendationType--><!--Device-RecommendationOptions-recommendationType?: RecommendationType-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## textContextInfo

```TypeScript
textContextInfo?: TextContextInfo
```

Text based on which images are recommended. If both **recommendationType** and **textContextInfo** are set, **textContextInfo** takes precedence over **recommendationType**.

**Type:** [TextContextInfo](arkts-medialibrary-photoaccesshelper-textcontextinfo-i.md)

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-RecommendationOptions-textContextInfo?: TextContextInfo--><!--Device-RecommendationOptions-textContextInfo?: TextContextInfo-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
