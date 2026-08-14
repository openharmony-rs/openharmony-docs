# DataMigrationProgress（系统接口）

描述数据迁移的进度信息，包含进度百分比和预估剩余时间。该接口为数据迁移回调onProgress方法的参数类型。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-fontManager-interface DataMigrationProgress--><!--Device-fontManager-interface DataMigrationProgress-End-->

**系统能力：** SystemCapability.Global.FontManager

**系统接口：** 此接口为系统接口。

## progressPercentage

```TypeScript
progressPercentage: int
```

数据迁移百分比进度，进度值根据已迁移的字体文件数量或大小计算，可能不是均匀增长。当progressPercentage为100时，迁移任务即将完成，onResult回调即将被调用。 取值范围为[0, 100]。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-DataMigrationProgress-progressPercentage: int--><!--Device-DataMigrationProgress-progressPercentage: int-End-->

**系统能力：** SystemCapability.Global.FontManager

**系统接口：** 此接口为系统接口。

## timeRemaining

```TypeScript
timeRemaining: int
```

预计剩余时间，可能因设备性能、文件大小、系统负载等因素而有所差异。 取值范围为非负整数，最小值为0。 单位为s。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-DataMigrationProgress-timeRemaining: int--><!--Device-DataMigrationProgress-timeRemaining: int-End-->

**系统能力：** SystemCapability.Global.FontManager

**系统接口：** 此接口为系统接口。

