# DistributedConfig

记录表的分布式配置信息。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-relationalStore-interface DistributedConfig--><!--Device-relationalStore-interface DistributedConfig-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## references

```TypeScript
references?: Array<Reference>
```

设置表之间的关联关系，可以设置多个字段的关联，子表和父表关联字段的值必须相同。默认数据库表之间无关联关系。 **系统接口：** 此接口为系统接口。 从API version 11开始，支持此可选参数。

**类型：** Array&lt;Reference&gt;

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-DistributedConfig-references?: Array<Reference>--><!--Device-DistributedConfig-references?: Array<Reference>-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**系统接口：** 此接口为系统接口。

