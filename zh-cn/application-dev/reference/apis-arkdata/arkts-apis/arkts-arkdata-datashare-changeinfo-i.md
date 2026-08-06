# ChangeInfo

数据变更时通知用户具体变更的内容，包括数据变更类型、变化的uri、变更的数据内容。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-dataShare-interface ChangeInfo--><!--Device-dataShare-interface ChangeInfo-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

## type

```TypeScript
type: ChangeType
```

通知变更的类型。

**类型：** ChangeType

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ChangeInfo-type: ChangeType--><!--Device-ChangeInfo-type: ChangeType-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

## uri

```TypeScript
uri: string
```

指定uri。

**类型：** string

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ChangeInfo-uri: string--><!--Device-ChangeInfo-uri: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

## values

```TypeScript
values: Array<ValuesBucket>
```

更新的数据。

**类型：** Array&lt;ValuesBucket&gt;

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ChangeInfo-values: Array<ValuesBucket>--><!--Device-ChangeInfo-values: Array<ValuesBucket>-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

