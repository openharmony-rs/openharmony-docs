# RdbDataChangeNode

订阅/取消订阅RDB数据变更的结果，回调支持传输不大于10M的数据。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-dataShare-interface RdbDataChangeNode--><!--Device-dataShare-interface RdbDataChangeNode-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

## data

```TypeScript
data: Array<string>
```

指定回调的数据。若处理回调数据时发生错误，则回调将不会被触发。

**类型：** Array&lt;string&gt;

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RdbDataChangeNode-data: Array<string>--><!--Device-RdbDataChangeNode-data: Array<string>-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

## templateId

```TypeScript
templateId: TemplateId
```

处理回调的templateId。

**类型：** TemplateId

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RdbDataChangeNode-templateId: TemplateId--><!--Device-RdbDataChangeNode-templateId: TemplateId-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

## uri

```TypeScript
uri: string
```

指定回调的uri。

**类型：** string

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RdbDataChangeNode-uri: string--><!--Device-RdbDataChangeNode-uri: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

