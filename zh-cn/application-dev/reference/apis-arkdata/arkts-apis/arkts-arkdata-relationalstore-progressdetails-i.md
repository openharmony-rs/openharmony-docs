# ProgressDetails

描述数据库整体执行端云同步任务上传和下载的统计信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-relationalStore-interface ProgressDetails--><!--Device-relationalStore-interface ProgressDetails-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## code

```TypeScript
code: ProgressCode
```

表示端云同步过程的状态。

**类型：** [ProgressCode](arkts-arkdata-relationalstore-progresscode-e.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ProgressDetails-code: ProgressCode--><!--Device-ProgressDetails-code: ProgressCode-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## details

```TypeScript
details: Record<string, TableDetails>
```

表示端云同步各表的统计信息。 键表示表名，值表示该表的端云同步过程统计信息。

**类型：** Record&lt;string, [TableDetails](arkts-arkdata-relationalstore-tabledetails-i.md)&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ProgressDetails-details: Record<string, TableDetails>--><!--Device-ProgressDetails-details: Record<string, TableDetails>-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## message

```TypeScript
message?: string
```

同步状态的详细消息。通过message信息查看详细的失败原因。默认值为空。

**类型：** string

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ProgressDetails-message?: string--><!--Device-ProgressDetails-message?: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## schedule

```TypeScript
schedule: Progress
```

表示端云同步过程。

**类型：** Progress

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ProgressDetails-schedule: Progress--><!--Device-ProgressDetails-schedule: Progress-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

