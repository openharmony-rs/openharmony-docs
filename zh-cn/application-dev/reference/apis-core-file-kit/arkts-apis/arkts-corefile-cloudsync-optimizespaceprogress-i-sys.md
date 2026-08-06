# OptimizeSpaceProgress（系统接口）

立即优化空间状态和当前进度。

**起始版本：** 17

**ArkTS模式：** ArkTS-Dyn起始版本为17；ArkTS-Sta起始版本为23。

<!--Device-cloudSync-interface OptimizeSpaceProgress--><!--Device-cloudSync-interface OptimizeSpaceProgress-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

## progress

```TypeScript
progress: int
```

优化进度百分比，范围[0,100]，单位：百分比。

**类型：** int

**起始版本：** 17

**ArkTS模式：** ArkTS-Dyn起始版本为17；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.CLOUDFILE_SYNC

<!--Device-OptimizeSpaceProgress-progress: int--><!--Device-OptimizeSpaceProgress-progress: int-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

## state

```TypeScript
state: OptimizeState
```

枚举值，优化空间状态。

**类型：** OptimizeState

**起始版本：** 17

**ArkTS模式：** ArkTS-Dyn起始版本为17；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.CLOUDFILE_SYNC

<!--Device-OptimizeSpaceProgress-state: OptimizeState--><!--Device-OptimizeSpaceProgress-state: OptimizeState-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

