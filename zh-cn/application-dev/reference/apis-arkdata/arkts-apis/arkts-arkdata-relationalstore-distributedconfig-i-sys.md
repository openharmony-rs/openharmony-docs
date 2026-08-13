# DistributedConfig

记录表的分布式配置信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-relationalStore-interface DistributedConfig--><!--Device-relationalStore-interface DistributedConfig-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## references

```TypeScript
references?: Array<Reference>
```

设置表之间的关联关系，可以设置多个字段的关联，子表和父表关联字段的值必须相同。默认数据库表之间无关联关系。 **系统接口：** 此接口为系统接口。 从API version 11开始，支持此可选参数。

**类型：** Array&lt;[Reference](arkts-arkdata-relationalstore-reference-i-sys.md)&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-DistributedConfig-references?: Array<Reference>--><!--Device-DistributedConfig-references?: Array<Reference>-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**系统接口：** 此接口为系统接口。

