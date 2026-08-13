# Value

存储在数据库中的值对象。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-distributedKVStore-interface Value--><!--Device-distributedKVStore-interface Value-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

## type

```TypeScript
type: ValueType
```

值类型。

**类型：** ValueType

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Value-type: ValueType--><!--Device-Value-type: ValueType-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

## value

```TypeScript
value: Uint8Array | string | long | double | boolean
```

键值对中的值。Uint8Array、string类型的长度范围为0-[MAX_VALUE_LENGTH](arkts-arkdata-distributedkvstore-constants-i.md#Constants)，number和boolean类型的取值范围由其自 身类型决定。

**类型：** Uint8Array \| string \| long \| double \| boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Value-value: Uint8Array | string | long | double | boolean--><!--Device-Value-value: Uint8Array | string | long | double | boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

