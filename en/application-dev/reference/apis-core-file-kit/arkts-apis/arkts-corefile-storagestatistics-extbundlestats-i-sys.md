# ExtBundleStats (System API)

```TypeScript
export interface ExtBundleStats
```

Details the space usage of system applications or system services.

**Since:** 23

<!--Device-storageStatistics-export interface ExtBundleStats--><!--Device-storageStatistics-export interface ExtBundleStats-End-->

**System capability:** SystemCapability.FileManagement.StorageService.SpatialStatistics

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { storageStatistics } from '@kit.CoreFileKit';
```

## businessName

```TypeScript
businessName: string
```

System application bundle name or system service name.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-ExtBundleStats-businessName: string--><!--Device-ExtBundleStats-businessName: string-End-->

**System capability:** SystemCapability.FileManagement.StorageService.SpatialStatistics

**System API:** This is a system API.

## flag

```TypeScript
flag: boolean
```

Whether the space occupied by system applications or system services needs to be displayed separately on the **Settings**  
> **Storage** page. A value of **true** enables independent display; a value of **false** merges the usage data into the application specified by **businessName**.

**Type:** boolean

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-ExtBundleStats-flag: boolean--><!--Device-ExtBundleStats-flag: boolean-End-->

**System capability:** SystemCapability.FileManagement.StorageService.SpatialStatistics

**System API:** This is a system API.

## size

```TypeScript
size: number
```

The business size. <br>Unit: Byte.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-ExtBundleStats-size: long--><!--Device-ExtBundleStats-size: long-End-->

**System capability:** SystemCapability.FileManagement.StorageService.SpatialStatistics

**System API:** This is a system API.
