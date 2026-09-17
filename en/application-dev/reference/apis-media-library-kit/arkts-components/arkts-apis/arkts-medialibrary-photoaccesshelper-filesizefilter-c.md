# FileSizeFilter

Describes the configuration for file size filtering.

**Since:** 19

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

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## fileSize

```TypeScript
fileSize: number
```

File size used for filtering.

The unit is bytes.

**Type:** number

**Since:** 19

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## filterOperator

```TypeScript
filterOperator: FilterOperator
```

Filter operator.

For example, files can be filtered based on being greater than or less than a certain file size.

**Type:** [FilterOperator](arkts-medialibrary-photoaccesshelper-filteroperator-e.md)

**Since:** 19

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
