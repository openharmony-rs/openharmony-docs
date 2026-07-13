# Value

存储在数据库中的值对象。

**起始版本：** 9

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

## type

```TypeScript
type: ValueType
```

值类型。

**类型：** ValueType

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

## value

```TypeScript
value: Uint8Array | string | number | number | boolean
```

键值对中的值。Uint8Array、string类型的长度范围为0-[MAX_VALUE_LENGTH](arkts-arkdata-constants-i.md)，number和boolean类型的取值范围由其自
身类型决定。

**类型：** Uint8Array | string | number | number | boolean

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

