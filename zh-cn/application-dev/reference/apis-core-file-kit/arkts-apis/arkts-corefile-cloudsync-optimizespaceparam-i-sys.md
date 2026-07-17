# OptimizeSpaceParam（系统接口）

立即优化空间设置参数，设置优化总空间和老化天数。

**起始版本：** 17

<!--Device-cloudSync-interface OptimizeSpaceParam--><!--Device-cloudSync-interface OptimizeSpaceParam-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { cloudSync } from '@kit.CoreFileKit';
```

## agingDays

```TypeScript
agingDays: number
```

老化天数。系统会以当前时间为基准，优化老化天数前未访问、已同步云空间的本地图片/视频，单位：天。

**类型：** number

**起始版本：** 17

**需要权限：** ohos.permission.CLOUDFILE_SYNC

<!--Device-OptimizeSpaceParam-agingDays: int--><!--Device-OptimizeSpaceParam-agingDays: int-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

## totalSize

```TypeScript
totalSize:number
```

优化空间总大小。查询媒体库接口获得需要老化的所有文件总大小，由应用传入，单位byte。

**类型：** number

**起始版本：** 17

**需要权限：** ohos.permission.CLOUDFILE_SYNC

<!--Device-OptimizeSpaceParam-totalSize:long--><!--Device-OptimizeSpaceParam-totalSize:long-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

