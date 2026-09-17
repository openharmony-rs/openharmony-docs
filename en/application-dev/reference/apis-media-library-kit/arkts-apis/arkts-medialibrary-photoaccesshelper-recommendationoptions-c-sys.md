# RecommendationOptions

Defines the image recommendation options. The image recommendation feature depends on the image data analysis capability, which varies with devices.

**Since:** 11

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## defaultRecommendationType

```TypeScript
defaultRecommendationType?: RecommendationType
```

Recommended tag displayed when the picker is opened. This configuration takes effect only after **recommendationTypeList** is set.

If the tag exists, the tag page is displayed by default.

If the tag does not exist, the All tag page is displayed by default.

**Type:** [RecommendationType](arkts-medialibrary-photoaccesshelper-recommendationtype-e.md)

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## recommendationTypeList

```TypeScript
recommendationTypeList?: Array<RecommendationType>
```

List of recommendation types. If images of multiple categories need to be recommended based on the enumerated value, set this parameter.

**Type:** Array&lt;[RecommendationType](arkts-medialibrary-photoaccesshelper-recommendationtype-e.md)&gt;

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.
