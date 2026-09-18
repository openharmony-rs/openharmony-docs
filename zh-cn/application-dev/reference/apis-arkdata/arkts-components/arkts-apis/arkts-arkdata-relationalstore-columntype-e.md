# ColumnType

描述数据库列存储类型的枚举。请使用枚举名称而非枚举值。

**起始版本：** 18

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## NULL

```TypeScript
NULL = 0
```

表示列数据类型为NULL。

**起始版本：** 18

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## INTEGER

```TypeScript
INTEGER = 1
```

表示列数据类型为64位整数。可用于保存8位（包括布尔值）、16位、32位、64位整数。如果64位整数大于2^53或小于-2^53，需使用[getString](arkts-arkdata-relationalstore-resultset-i.md#getstring)将64位整数转换为字符串。

**起始版本：** 18

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## REAL

```TypeScript
REAL = 2
```

表示列类型为浮点数。

**起始版本：** 18

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## TEXT

```TypeScript
TEXT = 3
```

表示列类型为字符串。

**起始版本：** 18

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## BLOB

```TypeScript
BLOB = 4
```

表示列类型为Uint8Array。

**起始版本：** 18

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## ASSET

```TypeScript
ASSET = 5
```

表示列类型为[Asset](arkts-arkdata-relationalstore-asset-i.md)。

**起始版本：** 18

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## ASSETS

```TypeScript
ASSETS = 6
```

表示列类型为[Assets](arkts-arkdata-relationalstore-assets-t.md)。

**起始版本：** 18

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## FLOAT_VECTOR

```TypeScript
FLOAT_VECTOR = 7
```

表示列类型为Float32Array。

**起始版本：** 18

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## UNLIMITED_INT

```TypeScript
UNLIMITED_INT = 8
```

表示列类型为bigint。

**起始版本：** 18

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core
