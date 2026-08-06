# ChangeInfo

记录端云同步过程详情。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-relationalStore-interface ChangeInfo--><!--Device-relationalStore-interface ChangeInfo-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## deleted

```TypeScript
deleted: Array<string> | Array<long>
```

记录删除数据的位置，如果该表的主键是string类型，该值是主键的值，否则该值表示删除数据的行号。

**类型：** Array&lt;string&gt; \| Array&lt;long&gt;

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-ChangeInfo-deleted: Array<string> | Array<long>--><!--Device-ChangeInfo-deleted: Array<string> | Array<long>-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## inserted

```TypeScript
inserted: Array<string> | Array<long>
```

记录插入数据的位置，如果该表的主键是string类型，该值是主键的值，否则该值表示插入数据的行号。

**类型：** Array&lt;string&gt; \| Array&lt;long&gt;

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-ChangeInfo-inserted: Array<string> | Array<long>--><!--Device-ChangeInfo-inserted: Array<string> | Array<long>-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## table

```TypeScript
table: string
```

表示发生变化的表的名称。

**类型：** string

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-ChangeInfo-table: string--><!--Device-ChangeInfo-table: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## type

```TypeScript
type: ChangeType
```

表示发生变化的数据的类型，数据或者资产附件发生变化。

**类型：** ChangeType

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-ChangeInfo-type: ChangeType--><!--Device-ChangeInfo-type: ChangeType-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## updated

```TypeScript
updated: Array<string> | Array<long>
```

记录更新数据的位置，如果该表的主键是string类型，该值是主键的值，否则该值表示更新数据的行号。

**类型：** Array&lt;string&gt; \| Array&lt;long&gt;

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-ChangeInfo-updated: Array<string> | Array<long>--><!--Device-ChangeInfo-updated: Array<string> | Array<long>-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

