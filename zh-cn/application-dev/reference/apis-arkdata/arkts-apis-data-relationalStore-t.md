# Types

> **说明：**
> 
> 本模块首批接口从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## Assets<sup>10+</sup>

type Assets = Asset[]

表示[Asset](arkts-apis-data-relationalStore-i.md#asset10)类型的数组。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

| 类型    | 说明                 |
| ------- | -------------------- |
| [Asset](arkts-apis-data-relationalStore-i.md#asset10)[] | 表示Asset类型的数组。   |

## ValueType

type ValueType = null | number | string | boolean | Uint8Array | Asset | Assets | Float32Array | bigint

用于表示允许的数据字段类型，接口参数具体类型根据其功能而定。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

| 类型    | 说明                 |
| ------- | -------------------- |
| null<sup>10+</sup>    | 表示值类型为空。   |
| number  | 表示值类型为数字。   |
| string  | 表示值类型为字符串。  |
| boolean | 表示值类型为布尔值。 |
| Uint8Array<sup>10+</sup>           | 表示值类型为Uint8类型的数组。            |
| Asset<sup>10+</sup>  | 表示值类型为附件[Asset](arkts-apis-data-relationalStore-i.md#asset10)。<br/>当字段类型是Asset时，在创建表的sql语句中，类型应当为：ASSET。 |
| Assets<sup>10+</sup> | 表示值类型为附件数组[Assets](#assets10)。<br/>当字段类型是Assets时，在创建表的sql语句中，类型应当为：ASSETS。 |
| Float32Array<sup>12+</sup> | 表示值类型为浮点数组。<br/>当字段类型是Float32Array时，在创建表的sql语句中，类型应当为：floatvector(128)。 |
| bigint<sup>12+</sup> | 表示值类型为任意长度的整数。<br/>当字段类型是bigint时，在创建表的sql语句中，类型应当为：UNLIMITED INT，详见[通过关系型数据库实现数据持久化](../../database/data-persistence-by-rdb-store.md)。<br/>**说明：** bigint类型字段不能比较大小，不适用以下谓词操作：between、notBetween、greaterThan、lessThan、greaterThanOrEqualTo、lessThanOrEqualTo、orderByAsc、orderByDesc。<br/>bigint类型字段的数据写入时，需通过BigInt()方法或在数据尾部添加'n'的方式明确为bigint类型，如'let data = BigInt(1234)'或'let data = 1234n'。<br/>bigint字段如果写入number类型的数据，则查询该数据的返回类型为number，而非bigint。 |

## ValuesBucket

type ValuesBucket = Record<string, ValueType>

用于存储键值对的类型。不支持Sendable跨线程传递。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

| 类型              | 说明                           |
| ---------------- | ---------------------------- |
| Record<string, [ValueType](#valuetype)> | 表示键值对类型。键的类型为string，值的类型为[ValueType](#valuetype)。 |

## PRIKeyType<sup>10+</sup> 

type PRIKeyType = number | string

用于表示数据库表某一行主键的数据类型。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

| 类型             | 说明                               |
| ---------------- | ---------------------------------- |
| number | 主键的类型可以是number。 |
| string | 主键的类型可以是string。 |

## UTCTime<sup>10+</sup>

type UTCTime = Date

用于表示UTC类型时间的数据类型。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

| 类型 | 说明            |
| ---- | --------------- |
| Date | UTC类型的时间。 |

## ModifyTime<sup>10+</sup> 

type ModifyTime = Map<PRIKeyType, UTCTime>

用于存储数据库表的主键和修改时间的数据类型。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

| 类型                                                    | 说明                                                         |
| ------------------------------------------------------- | ------------------------------------------------------------ |
| Map<[PRIKeyType](#prikeytype10), [UTCTime](#utctime10)> | 键表示是数据库表某一行的主键，值表示该行的最后修改时间，用UTC格式表示。 |
