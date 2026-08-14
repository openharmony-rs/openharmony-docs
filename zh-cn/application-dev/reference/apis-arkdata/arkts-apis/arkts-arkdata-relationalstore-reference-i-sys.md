# Reference（系统接口）

记录表之间通过表字段指定的关联关系。其中表a关联到表b，称a为b关联的子表，b为a关联的父表。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-relationalStore-interface Reference--><!--Device-relationalStore-interface Reference-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**系统接口：** 此接口为系统接口。

## refFields

```TypeScript
refFields: Record<string, string>
```

表示关联表的关联字段。键值数据中键为子表字段，值为父表字段。

**类型：** Record&lt;string, string&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Reference-refFields: Record<string, string>--><!--Device-Reference-refFields: Record<string, string>-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**系统接口：** 此接口为系统接口。

## sourceTable

```TypeScript
sourceTable: string
```

关联的子表名称。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Reference-sourceTable: string--><!--Device-Reference-sourceTable: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**系统接口：** 此接口为系统接口。

## targetTable

```TypeScript
targetTable: string
```

关联的父表名称。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Reference-targetTable: string--><!--Device-Reference-targetTable: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**系统接口：** 此接口为系统接口。

