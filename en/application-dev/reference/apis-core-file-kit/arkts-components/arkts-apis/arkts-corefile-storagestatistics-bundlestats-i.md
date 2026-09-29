# BundleStats

```TypeScript
export interface BundleStats
```

Get the bundle statistics.

**Since:** 9

<!--Device-storageStatistics-export interface BundleStats--><!--Device-storageStatistics-export interface BundleStats-End-->

**System capability:** SystemCapability.FileManagement.StorageService.SpatialStatistics

## Modules to Import

```TypeScript
import { storageStatistics } from '@kit.CoreFileKit';
```

## appSize

```TypeScript
appSize: number
```

The size of application installation data. <br>Unit: Byte.

**Type:** number

**Since:** 9

<!--Device-BundleStats-appSize: long--><!--Device-BundleStats-appSize: long-End-->

**System capability:** SystemCapability.FileManagement.StorageService.SpatialStatistics

## cacheSize

```TypeScript
cacheSize: number
```

The size of application cache data. <br>Unit: Byte.

**Type:** number

**Since:** 9

<!--Device-BundleStats-cacheSize: long--><!--Device-BundleStats-cacheSize: long-End-->

**System capability:** SystemCapability.FileManagement.StorageService.SpatialStatistics

## dataSize

```TypeScript
dataSize: number
```

The size of application local data, distributed data and database data. <br>Unit: Byte.

**Type:** number

**Since:** 9

<!--Device-BundleStats-dataSize: long--><!--Device-BundleStats-dataSize: long-End-->

**System capability:** SystemCapability.FileManagement.StorageService.SpatialStatistics
