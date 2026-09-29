# FileSizeFilter

```TypeScript
class FileSizeFilter
```

Describes the configuration for file size filtering.

**Since:** 19

<!--Device-photoAccessHelper-class FileSizeFilter--><!--Device-photoAccessHelper-class FileSizeFilter-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## extraFileSize

```TypeScript
extraFileSize?: number
```

Maximum file size in **FilterOperator.BETWEEN** mode. The default value is **-1**.

The unit is bytes.

**Type:** number

**Since:** 19

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-FileSizeFilter-extraFileSize?: long--><!--Device-FileSizeFilter-extraFileSize?: long-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## fileSize

```TypeScript
fileSize: number
```

File size used for filtering.

The unit is bytes.

**Type:** number

**Since:** 19

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-FileSizeFilter-fileSize: long--><!--Device-FileSizeFilter-fileSize: long-End-->

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

<!--Device-FileSizeFilter-filterOperator: FilterOperator--><!--Device-FileSizeFilter-filterOperator: FilterOperator-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
