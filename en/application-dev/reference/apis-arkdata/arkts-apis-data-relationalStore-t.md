# Types

<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @htt1997-->
<!--Tester: @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=8af95004d9117739e6649a82566e8756f994e75a translatedAt=2026-07-14T10:28:10.883Z pushedAt=2026-07-17T09:25:12.103Z -->

> **NOTE**
> 
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Assets<sup>10+</sup>

type Assets = Asset[]

Indicates an [Asset](arkts-apis-data-relationalStore-i.md#asset10) array.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

| Type   | Description                |
| ------- | -------------------- |
| [Asset](arkts-apis-data-relationalStore-i.md#asset10)[] | Array of assets.  |

## ValueType

type ValueType = null | number | string | boolean | Uint8Array | Asset | Assets | Float32Array | bigint

Defines the types of the value in a KV pair. The type varies with the parameter function.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

| Type   | Description                |
| ------- | -------------------- |
| null    | Null.   |
| number  | Number.  |
| string  | String. |
| boolean | Boolean.|
| Uint8Array           | Uint8 array.            |
| Asset<sup>10+</sup>  | [Asset](arkts-apis-data-relationalStore-i.md#asset10).<br/>When the field type is Asset, the type should be ASSET in the SQL statement for creating a table. |
| Assets<sup>10+</sup> | [Assets](#assets10).<br/>When the field type is Assets, the type should be ASSETS in the SQL statement for creating a table. |
| Float32Array<sup>12+</sup> | Array of 32-bit floating-point numbers.<br/>When the field type is Float32Array, the type should be floatvector(128) in the SQL statement for creating a table. |
| bigint<sup>12+</sup> | Integer of any length.<br/>When the field type is bigint, the type should be UNLIMITED INT in the SQL statement for creating a table. For details, see [Data Persistence by Relational Database](../../database/data-persistence-by-rdb-store.md).<br/>**NOTE**<br/>Fields of the bigint type cannot be compared in size and do not support the following predicate operations: **between**, **notBetween**, **greaterThan**, **lessThan**, **greaterThanOrEqualTo**, **lessThanOrEqualTo**, **orderByAsc**, and **orderByDesc**.<br/>When writing data to a bigint field, you must explicitly specify the bigint type by using the **BigInt()** method or appending **n** to the data, for example, **let data = BigInt(1234)** or **let data = 1234n**.<br/>If data of the number type is written to a bigint field, the type of the data returned by the query is number instead of bigint. |

## ValuesBucket

type ValuesBucket = Record<string, ValueType>

Defines the data in the form of a KV pair. **ValuesBucket** cannot be passed across threads using Sendable.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

| Type             | Description                          |
| ---------------- | ---------------------------- |
| Record<string, [ValueType](#valuetype)> | Types of the key and value in a KV pair. The key type is string, and the value type is [ValueType](#valuetype).|

## PRIKeyType<sup>10+</sup>

type PRIKeyType = number | string

Enumerates the types of the primary key in a row of a database table.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

| Type            | Description                              |
| ---------------- | ---------------------------------- |
| number | The primary key is a number.|
| string | The primary key is a string.|

## UTCTime<sup>10+</sup>

type UTCTime = Date

Represents the data type of UTC time.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

| Type| Description           |
| ---- | --------------- |
| Date | UTC time. |

## ModifyTime<sup>10+</sup>

type ModifyTime = Map<PRIKeyType, UTCTime>

Represents the data type of the primary key and modification time of a database table.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

| Type                                                   | Description                                                        |
| ------------------------------------------------------- | ------------------------------------------------------------ |
| Map<[PRIKeyType](#prikeytype10), [UTCTime](#utctime10)> | The key is the primary key of a row in a database table, and the value is the last modification time of the row, in UTC format. |

## RowData<sup>23+</sup>

type RowData = Array\<ValueType>

Defines a row of data in a database table.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

| Type             | Description                          |
| ---------------- | ---------------------------- |
| Array<[ValueType](#valuetype)> | Array of the types of [ValueType](#valuetype).|

## RowsData<sup>23+</sup>

type RowsData = Array\<RowData>

Defines multiple rows of data in a database table.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

| Type             | Description                          |
| ---------------- | ---------------------------- |
| Array<[RowData](#rowdata23)> | Array of the [RowData](#rowdata23) types.|