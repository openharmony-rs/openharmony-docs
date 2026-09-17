# ColumnType

Enumerates the types of the column data. Use the enum name rather than the enum value.

**Since:** 18

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## NULL

```TypeScript
NULL = 0
```

The value in the column is null.

**Since:** 18

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## INTEGER

```TypeScript
INTEGER = 1
```

64-bit integer.

The column can hold 8-bit (including Boolean values), 16-bit, 32-bit, and 64-bit integers. If the 64-bit integer is greater than 2^53 or less than -2^53, use [getString](arkts-arkdata-relationalstore-resultset-i.md#getstring) to convert the 64-bit integer to a string.

**Since:** 18

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## REAL

```TypeScript
REAL = 2
```

The value in the column is a floating point number.

**Since:** 18

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## TEXT

```TypeScript
TEXT = 3
```

The value in the column is a string.

**Since:** 18

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## BLOB

```TypeScript
BLOB = 4
```

The value in the column is a Uint8Array.

**Since:** 18

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## ASSET

```TypeScript
ASSET = 5
```

The value in the column is an asset.

**Since:** 18

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## ASSETS

```TypeScript
ASSETS = 6
```

The value in the column is an array of assets.

**Since:** 18

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## FLOAT_VECTOR

```TypeScript
FLOAT_VECTOR = 7
```

The value in the column is a Float32Array.

**Since:** 18

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## UNLIMITED_INT

```TypeScript
UNLIMITED_INT = 8
```

The value in the column is a bigint.

**Since:** 18

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core
