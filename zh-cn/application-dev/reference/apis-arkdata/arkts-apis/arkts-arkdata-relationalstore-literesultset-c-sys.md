# LiteResultSet

提供查询数据库后生成的结果集的访问方法。结果集是指用户调用关系型数据库查询接口之后返回的结果集合，提供了多种灵活的数据访问方式，以便用户获取各项数据。 LiteResultSet实例不会实时刷新。使用结果集后，如果数据库中的数据发生变化（如增删改操作），需要重新查询才能获取到最新的数据。 下列API示例中，都需先使用[queryWithoutRowCount]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_、 [querySqlWithoutRowCount]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_等query类方法中任一方法获取到LiteResultSet实例，再 通过此实例调用对应方法。 > **说明：** > > - 本class首批接口从API version 23开始支持。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-relationalStore-class LiteResultSet--><!--Device-relationalStore-class LiteResultSet-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## getFloat32Array

ArkTS-Dyn:
```TypeScript
getFloat32Array(columnIndex: number): Float32Array
```

ArkTS-Sta:
```TypeScript
getFloat32Array(columnIndex: int): Float32Array
```

以浮点数组的形式获取当前行中指定列的值，仅在向量数据库（在[StoreConfig]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_中配置vector为true）下可用。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LiteResultSet-getFloat32Array(columnIndex: int): Float32Array--><!--Device-LiteResultSet-getFloat32Array(columnIndex: int): Float32Array-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| columnIndex | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 指定的列索引，从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Float32Array | 以浮点数组的形式返回指定列的值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指定位置不合法) | ResultSet is empty or pointer index is out of bounds. |
| [14800013](../errorcode-data-rdb.md#14800013-列值为空或列类型与当前调用接口不兼容) | Column index is out of bounds. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800041](../errorcode-data-rdb.md#14800041-类型转换失败) | Type conversion failed. |

