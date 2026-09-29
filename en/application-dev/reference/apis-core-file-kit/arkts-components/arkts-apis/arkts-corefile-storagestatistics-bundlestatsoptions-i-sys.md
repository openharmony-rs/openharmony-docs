# BundleStatsOptions (System API)

```TypeScript
export interface BundleStatsOptions
```

Options for obtaining the bundle statistics.

**Since:** 26.0.1

<!--Device-storageStatistics-export interface BundleStatsOptions--><!--Device-storageStatistics-export interface BundleStatsOptions-End-->

**System capability:** SystemCapability.FileManagement.StorageService.SpatialStatistics

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { storageStatistics } from '@kit.CoreFileKit';
```

## index

```TypeScript
index?: number
```

Index of an application clone. The default value is **0**, which indicates the application itself. When an application clone is created, an index is assigned from 1 sequentially to **appIndex** of [BundleResourceInfo](../../apis-ability-kit/arkts-apis/arkts-ability-bundleresourceinfo-i-sys.md).

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-BundleStatsOptions-index?: int--><!--Device-BundleStatsOptions-index?: int-End-->

**System capability:** SystemCapability.FileManagement.StorageService.SpatialStatistics

**System API:** This is a system API.

## statFlag

```TypeScript
statFlag?: GetBundleStatsFlag
```

Flag for obtaining the bundle statistics.

**Type:** [GetBundleStatsFlag](arkts-corefile-storagestatistics-getbundlestatsflag-e-sys.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-BundleStatsOptions-statFlag?: GetBundleStatsFlag--><!--Device-BundleStatsOptions-statFlag?: GetBundleStatsFlag-End-->

**System capability:** SystemCapability.FileManagement.StorageService.SpatialStatistics

**System API:** This is a system API.
