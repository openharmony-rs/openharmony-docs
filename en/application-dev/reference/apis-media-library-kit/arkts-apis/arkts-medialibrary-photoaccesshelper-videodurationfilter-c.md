# VideoDurationFilter

```TypeScript
class VideoDurationFilter
```

Describes the configuration for video duration filtering.

**Since:** 19

<!--Device-photoAccessHelper-class VideoDurationFilter--><!--Device-photoAccessHelper-class VideoDurationFilter-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## extraVideoDuration

```TypeScript
extraVideoDuration?: number
```

Maximum video duration in **FilterOperator.BETWEEN** mode. The default value is **-1**.

The unit is milliseconds (ms).

**Type:** number

**Since:** 19

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-VideoDurationFilter-extraVideoDuration?: int--><!--Device-VideoDurationFilter-extraVideoDuration?: int-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## filterOperator

```TypeScript
filterOperator: FilterOperator
```

Filter operator.

For example, files can be filtered based on being greater than or less than a certain file size.

**Type:** [FilterOperator](arkts-medialibrary-photoaccesshelper-filteroperator-e.md)

**Since:** 19

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-VideoDurationFilter-filterOperator: FilterOperator--><!--Device-VideoDurationFilter-filterOperator: FilterOperator-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## videoDuration

```TypeScript
videoDuration: number
```

Video duration used for filtering.

The unit is milliseconds (ms).

**Type:** number

**Since:** 19

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-VideoDurationFilter-videoDuration: int--><!--Device-VideoDurationFilter-videoDuration: int-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
