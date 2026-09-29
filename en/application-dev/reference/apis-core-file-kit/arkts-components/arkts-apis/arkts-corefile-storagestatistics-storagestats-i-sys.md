# StorageStats (System API)

```TypeScript
export interface StorageStats
```

Get the user storage statistics.

**Since:** 9

<!--Device-storageStatistics-export interface StorageStats--><!--Device-storageStatistics-export interface StorageStats-End-->

**System capability:** SystemCapability.FileManagement.StorageService.SpatialStatistics

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { storageStatistics } from '@kit.CoreFileKit';
```

## app

```TypeScript
app: number
```

The size of application. <br>Unit: Byte.

**Type:** number

**Since:** 9

<!--Device-StorageStats-app: long--><!--Device-StorageStats-app: long-End-->

**System capability:** SystemCapability.FileManagement.StorageService.SpatialStatistics

**System API:** This is a system API.

## audio

```TypeScript
audio: number
```

The size of audio file. <br>Unit: Byte.

**Type:** number

**Since:** 9

<!--Device-StorageStats-audio: long--><!--Device-StorageStats-audio: long-End-->

**System capability:** SystemCapability.FileManagement.StorageService.SpatialStatistics

**System API:** This is a system API.

## file

```TypeScript
file: number
```

The size of other file. <br>Unit: Byte.

**Type:** number

**Since:** 9

<!--Device-StorageStats-file: long--><!--Device-StorageStats-file: long-End-->

**System capability:** SystemCapability.FileManagement.StorageService.SpatialStatistics

**System API:** This is a system API.

## image

```TypeScript
image: number
```

The size of image file. <br>Unit: Byte.

**Type:** number

**Since:** 9

<!--Device-StorageStats-image: long--><!--Device-StorageStats-image: long-End-->

**System capability:** SystemCapability.FileManagement.StorageService.SpatialStatistics

**System API:** This is a system API.

## total

```TypeScript
total: number
```

The total size of device. <br>Unit: Byte.

**Type:** number

**Since:** 9

<!--Device-StorageStats-total: long--><!--Device-StorageStats-total: long-End-->

**System capability:** SystemCapability.FileManagement.StorageService.SpatialStatistics

**System API:** This is a system API.

## video

```TypeScript
video: number
```

The size of video file. <br>Unit: Byte.

**Type:** number

**Since:** 9

<!--Device-StorageStats-video: long--><!--Device-StorageStats-video: long-End-->

**System capability:** SystemCapability.FileManagement.StorageService.SpatialStatistics

**System API:** This is a system API.
