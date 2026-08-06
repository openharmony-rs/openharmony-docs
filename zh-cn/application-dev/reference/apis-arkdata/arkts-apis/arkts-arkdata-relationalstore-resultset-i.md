# ResultSet

提供通过查询数据库生成的数据库结果集的访问方法。结果集是指用户调用关系型数据库查询接口之后返回的结果集合，提供了多种灵活的数据访问方式，以便用户获取各项数据。 ResultSet实例不会实时刷新。使用结果集后，如果数据库中的数据发生变化（如增删改操作），需要重新查询才能获取到最新的数据。 下列API示例中，都需先使用 [query]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ 、 [querySql]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_ 、 [remoteQuery]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_ 、[queryLockedRow]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_等query类方法中任一方法获取到ResultSet实例，再通过此实例调用对应方法。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-relationalStore-interface ResultSet--><!--Device-relationalStore-interface ResultSet-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## close

```TypeScript
close(): void
```

关闭结果集，若不关闭可能会引起FD（File Descriptor）泄漏和内存泄漏。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-ResultSet-close(): void--><!--Device-ResultSet-close(): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指定位置不合法) | ResultSet is empty or pointer index is out of bounds. |
| [14800000](../../apis-basic-services-kit/errorcode-settings.md#14800000-参数检查失败) | Inner error.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |

## getAsset

ArkTS-Dyn:
```TypeScript
getAsset(columnIndex: number): Asset
```

ArkTS-Sta:
```TypeScript
getAsset(columnIndex: int): Asset
```

以[Asset]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_形式获取当前行中指定列的值，如果当前列的数据类型为Asset类型，会以Asset类型返回指定值，如果当前列中的值为null时，会返回null，其他类型则 抛出错误码14800000。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-ResultSet-getAsset(columnIndex: int): Asset--><!--Device-ResultSet-getAsset(columnIndex: int): Asset-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| columnIndex | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 指定的列索引，从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 以Asset形式返回指定列的值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800013](../errorcode-data-rdb.md#14800013-列值为空或列类型与当前调用接口不兼容) | Column index is out of bounds. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../../apis-basic-services-kit/errorcode-settings.md#14800000-参数检查失败) | Inner error.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指定位置不合法) | ResultSet is empty or pointer index is out of bounds.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |

## getAssets

ArkTS-Dyn:
```TypeScript
getAssets(columnIndex: number): Assets
```

ArkTS-Sta:
```TypeScript
getAssets(columnIndex: int): Assets
```

以[Assets]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_形式获取当前行中指定列的值，如果当前列的数据类型为Assets类型，会以Assets类型返回指定值，如果当前列中的值为null时，会返回null，其 他类型则抛出14800000。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-ResultSet-getAssets(columnIndex: int): Assets--><!--Device-ResultSet-getAssets(columnIndex: int): Assets-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| columnIndex | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 指定的列索引，从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 以Assets形式返回指定列的值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800013](../errorcode-data-rdb.md#14800013-列值为空或列类型与当前调用接口不兼容) | Column index is out of bounds. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../../apis-basic-services-kit/errorcode-settings.md#14800000-参数检查失败) | Inner error.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指定位置不合法) | ResultSet is empty or pointer index is out of bounds.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |

## getBlob

ArkTS-Dyn:
```TypeScript
getBlob(columnIndex: number): Uint8Array
```

ArkTS-Sta:
```TypeScript
getBlob(columnIndex: int): Uint8Array
```

以字节数组的形式获取当前行中指定列的值，如果当前列的数据类型为INTEGER、DOUBLE、TEXT、BLOB类型，会转成字节数组类型返回指定值，如果该列内容为空时，会返回空字节数组，其他类型则抛出错误码14800000。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-ResultSet-getBlob(columnIndex: int): Uint8Array--><!--Device-ResultSet-getBlob(columnIndex: int): Uint8Array-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| columnIndex | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 指定的列索引，从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint8Array | 以字节数组的形式返回指定列的值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800013](../errorcode-data-rdb.md#14800013-列值为空或列类型与当前调用接口不兼容) | Column index is out of bounds. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../../apis-basic-services-kit/errorcode-settings.md#14800000-参数检查失败) | Inner error.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指定位置不合法) | ResultSet is empty or pointer index is out of bounds.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |

## getColumnIndex

ArkTS-Dyn:
```TypeScript
getColumnIndex(columnName: string): number
```

ArkTS-Sta:
```TypeScript
getColumnIndex(columnName: string): int
```

根据指定的列名获取列索引。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-ResultSet-getColumnIndex(columnName: string): int--><!--Device-ResultSet-getColumnIndex(columnName: string): int-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| columnName | string | 是 | 表示结果集中指定列的名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 返回指定列的索引。当结果集中包含重名列时，返回值会不符合预期。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800013](../errorcode-data-rdb.md#14800013-列值为空或列类型与当前调用接口不兼容) | Column index is out of bounds. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../../apis-basic-services-kit/errorcode-settings.md#14800000-参数检查失败) | Inner error.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800019](../errorcode-data-rdb.md#14800019-sql必须是查询语句) | The SQL must be a query statement.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |

## getColumnName

ArkTS-Dyn:
```TypeScript
getColumnName(columnIndex: number): string
```

ArkTS-Sta:
```TypeScript
getColumnName(columnIndex: int): string
```

根据指定的列索引获取列名。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-ResultSet-getColumnName(columnIndex: int): string--><!--Device-ResultSet-getColumnName(columnIndex: int): string-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| columnIndex | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 指定的列索引，从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回指定列的名称。当结果集中包含重名列时，返回值会不符合预期。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800013](../errorcode-data-rdb.md#14800013-列值为空或列类型与当前调用接口不兼容) | Column index is out of bounds. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../../apis-basic-services-kit/errorcode-settings.md#14800000-参数检查失败) | Inner error.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800019](../errorcode-data-rdb.md#14800019-sql必须是查询语句) | The SQL must be a query statement.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |

## getColumnNames

```TypeScript
getColumnNames(): Array<string>
```

获取结果集中所有列的名称。 列名以字符串数组的形式返回，数组中字符串的顺序与结果集中列的顺序一致。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ResultSet-getColumnNames(): Array<string>--><!--Device-ResultSet-getColumnNames(): Array<string>-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | 返回结果集中所有列的名称。支持获取包含重名列的列名。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800019](../errorcode-data-rdb.md#14800019-sql必须是查询语句) | The SQL must be a query statement. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file. |

## getColumnType

ArkTS-Dyn:
```TypeScript
getColumnType(columnIdentifier: number | string): Promise<ColumnType>
```

ArkTS-Sta:
```TypeScript
getColumnType(columnIdentifier: int | string): Promise<ColumnType>
```

根据指定的列索引或列名称获取列数据类型，使用Promise异步回调。

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-ResultSet-getColumnType(columnIdentifier: int | string): Promise<ColumnType>--><!--Device-ResultSet-getColumnType(columnIdentifier: int | string): Promise<ColumnType>-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| columnIdentifier | ArkTS-Dyn: number \| string  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int \| string | 是 | 表示结果集中指定列的索引或列名。索引必须是非负整数，且必须小于属性columnNames的长度。列名必须是属性columnNames内的名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ColumnType&gt; | Promise对象。返回指定列的数据类型。当结果集中包含重名列时，通过列名获取的结果会不符合预期，建议使用列索引形式获取。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../../apis-basic-services-kit/errorcode-settings.md#14800000-参数检查失败) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指定位置不合法) | ResultSet is empty or pointer index is out of bounds. |
| [14800013](../errorcode-data-rdb.md#14800013-列值为空或列类型与当前调用接口不兼容) | Column index is out of bounds. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800019](../errorcode-data-rdb.md#14800019-sql必须是查询语句) | The SQL must be a query statement. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch. |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly. |

## getColumnTypeSync

ArkTS-Dyn:
```TypeScript
getColumnTypeSync(columnIdentifier: number | string): ColumnType
```

ArkTS-Sta:
```TypeScript
getColumnTypeSync(columnIdentifier: int | string): ColumnType
```

根据指定的列索引或列名称获取列数据类型。

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-ResultSet-getColumnTypeSync(columnIdentifier: int | string): ColumnType--><!--Device-ResultSet-getColumnTypeSync(columnIdentifier: int | string): ColumnType-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| columnIdentifier | ArkTS-Dyn: number \| string  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int \| string | 是 | 表示结果集中指定列的索引或名称。索引必须是非负整数，最大不能超过属性columnNames的长度。列名必须是属性columnNames内的名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回指定列的数据类型。当结果集中包含重名列时，通过列名获取的结果会不符合预期，建议使用列索引形式获取。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../../apis-basic-services-kit/errorcode-settings.md#14800000-参数检查失败) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指定位置不合法) | ResultSet is empty or pointer index is out of bounds. |
| [14800013](../errorcode-data-rdb.md#14800013-列值为空或列类型与当前调用接口不兼容) | Column index is out of bounds. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800019](../errorcode-data-rdb.md#14800019-sql必须是查询语句) | The SQL must be a query statement. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch. |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly. |

## getCurrentRowData

```TypeScript
getCurrentRowData(): RowData
```

获取当前行所有列的值。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ResultSet-getCurrentRowData(): RowData--><!--Device-ResultSet-getCurrentRowData(): RowData-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回当前行所有列的值。支持获取包含重名列的值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指定位置不合法) | ResultSet is empty or pointer index is out of bounds. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800019](../errorcode-data-rdb.md#14800019-sql必须是查询语句) | The SQL must be a query statement. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file. |

## getDouble

ArkTS-Dyn:
```TypeScript
getDouble(columnIndex: number): number
```

ArkTS-Sta:
```TypeScript
getDouble(columnIndex: int): double
```

以double形式获取当前行中指定列的值，如果当前列的数据类型为INTEGER、DOUBLE、TEXT、BLOB类型，会转成double类型返回指定值，如果该列内容为空时，会返回0.0，其他类型则抛出错误码14800000。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-ResultSet-getDouble(columnIndex: int): double--><!--Device-ResultSet-getDouble(columnIndex: int): double-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| columnIndex | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 指定的列索引，从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 以double形式返回指定列的值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800013](../errorcode-data-rdb.md#14800013-列值为空或列类型与当前调用接口不兼容) | Column index is out of bounds. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../../apis-basic-services-kit/errorcode-settings.md#14800000-参数检查失败) | Inner error.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指定位置不合法) | ResultSet is empty or pointer index is out of bounds.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |

## getLong

ArkTS-Dyn:
```TypeScript
getLong(columnIndex: number): number
```

ArkTS-Sta:
```TypeScript
getLong(columnIndex: int): long
```

以Long形式获取当前行中指定列的值，如果当前列的数据类型为INTEGER、DOUBLE、TEXT、BLOB类型，会转成Long类型返回指定值，如果该列内容为空时，会返回0，其他类型则抛出错误码14800000。如果当前列的数 据类型为INTEGER，值大于 Number.MAX\_SAFE\_INTEGER 或小于 Number.MIN\_SAFE\_INTEGER 且不希望丢失精度，建议使用 [getString]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_接口获取。如果当前列的数据类型为DOUBLE且不希望丢失精度，建议使用 [getDouble]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_接口获取。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-ResultSet-getLong(columnIndex: int): long--><!--Device-ResultSet-getLong(columnIndex: int): long-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| columnIndex | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 指定的列索引，从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：long | 以Long形式返回指定列的值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800013](../errorcode-data-rdb.md#14800013-列值为空或列类型与当前调用接口不兼容) | Column index is out of bounds. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../../apis-basic-services-kit/errorcode-settings.md#14800000-参数检查失败) | Inner error.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指定位置不合法) | ResultSet is empty or pointer index is out of bounds.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |

## getRow

```TypeScript
getRow(): ValuesBucket
```

获取当前行。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-ResultSet-getRow(): ValuesBucket--><!--Device-ResultSet-getRow(): ValuesBucket-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回指定行的值。当结果集中包含重名列时，返回值会不符合预期，建议使用 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800000](../../apis-basic-services-kit/errorcode-settings.md#14800000-参数检查失败) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指定位置不合法) | ResultSet is empty or pointer index is out of bounds.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800013](../errorcode-data-rdb.md#14800013-列值为空或列类型与当前调用接口不兼容) | Column index is out of bounds.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |

## getRows

ArkTS-Dyn:
```TypeScript
getRows(maxCount: number, position?: number): Promise<Array<ValuesBucket>>
```

ArkTS-Sta:
```TypeScript
getRows(maxCount: int, position?: int): Promise<Array<ValuesBucket>>
```

从结果集中获取指定数量的数据，使用Promise异步回调。禁止与[ResultSet]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_的其他接口并发调用，否则获取的数据可能非预期。

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-ResultSet-getRows(maxCount: int, position?: int): Promise<Array<ValuesBucket>>--><!--Device-ResultSet-getRows(maxCount: int, position?: int): Promise<Array<ValuesBucket>>-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| maxCount | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 正整数，指定要从结果集中获取数据的条数。不为正整数则参数非法，抛出错误码401。 |
| position | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 否 | 非负整数，指定从结果集中获取数据的起始位置，不填则从结果集的当前行（默认首次获取数据时为当前结果集的第一行）开始获取数据。不为非负整数则参数非法，抛出错误码401。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;ValuesBucket&gt;&gt; | 返回maxCount条数据，剩余数据不足maxCount条则返回剩余数据，返回空数组时代表已经遍历到结果集的末尾。当结果集中包含重名列时，返回 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../../apis-basic-services-kit/errorcode-settings.md#14800000-参数检查失败) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指定位置不合法) | ResultSet is empty or pointer index is out of bounds. |
| [14800013](../errorcode-data-rdb.md#14800013-列值为空或列类型与当前调用接口不兼容) | Column index is out of bounds. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch. |

## getRowsData

ArkTS-Dyn:
```TypeScript
getRowsData(maxCount: number, position?: number): Promise<RowsData>
```

ArkTS-Sta:
```TypeScript
getRowsData(maxCount: int, position?: int): Promise<RowsData>
```

从指定位置position开始，最多获取maxCount行数据。使用Promise异步回调。禁止与[ResultSet]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_的其他接口并发调用，否则获取的数据可能非 预期。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ResultSet-getRowsData(maxCount: int, position?: int): Promise<RowsData>--><!--Device-ResultSet-getRowsData(maxCount: int, position?: int): Promise<RowsData>-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| maxCount | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 正整数，指定从结果集中获取数据的条数。不为正整数则参数非法，抛出错误码14800001。 |
| position | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 否 | 非负整数，指定从结果集中获取数据的起始位置，不填则从结果集的当前行（默认首次获取数据时为当前结果集的第一行）开始获取数据。不为非负整数则参数非法，抛出错误码14800001。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;RowsData&gt; | 返回maxCount条数据，剩余数据不足maxCount条则返回剩余数据，返回空数组时代表已经遍历到结果集的末尾。支持获取包含重名列的值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指定位置不合法) | ResultSet is empty or pointer index is out of bounds. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800019](../errorcode-data-rdb.md#14800019-sql必须是查询语句) | The SQL must be a query statement. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit. |

## getSendableRow

```TypeScript
getSendableRow(): sendableRelationalStore.ValuesBucket
```

获取当前行数据的sendable形式，用于跨线程传递。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

<!--Device-ResultSet-getSendableRow(): sendableRelationalStore.ValuesBucket--><!--Device-ResultSet-getSendableRow(): sendableRelationalStore.ValuesBucket-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| sendableRelationalStore.ValuesBucket | 当前行数据的sendable形式，用于跨线程传递。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800000](../../apis-basic-services-kit/errorcode-settings.md#14800000-参数检查失败) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指定位置不合法) | ResultSet is empty or pointer index is out of bounds. |
| [14800013](../errorcode-data-rdb.md#14800013-列值为空或列类型与当前调用接口不兼容) | Column index is out of bounds. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch. |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly. |

## getString

ArkTS-Dyn:
```TypeScript
getString(columnIndex: number): string
```

ArkTS-Sta:
```TypeScript
getString(columnIndex: int): string
```

以字符串形式获取当前行中指定列的值，如果当前列中的值为INTEGER、DOUBLE、TEXT、BLOB类型，会以字符串形式返回指定值，如果是当前列中的值为INTEGER，并且为空，则会返回空字符串""，其他类型则抛出错误码14 800000。如果当前列中的值为DOUBLE类型，可能存在精度的丢失，建议使用[getDouble]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_接口获取。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-ResultSet-getString(columnIndex: int): string--><!--Device-ResultSet-getString(columnIndex: int): string-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| columnIndex | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 指定的列索引，从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 以字符串形式返回指定列的值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800013](../errorcode-data-rdb.md#14800013-列值为空或列类型与当前调用接口不兼容) | Column index is out of bounds. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../../apis-basic-services-kit/errorcode-settings.md#14800000-参数检查失败) | Inner error.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指定位置不合法) | ResultSet is empty or pointer index is out of bounds.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |

## getValue

ArkTS-Dyn:
```TypeScript
getValue(columnIndex: number): ValueType
```

ArkTS-Sta:
```TypeScript
getValue(columnIndex: int): ValueType
```

获取当前行中指定列的值，如果值类型是ValueType中指定的任意类型，返回指定类型的值，否则抛出错误码14800000。如果值类型为INTEGER，值大于 Number.MAX\_SAFE\_INTEGER 或小于 Number.MIN\_SAFE\_INTEGER 且不希望丢失精度，建议使用[getString]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_接口获取。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-ResultSet-getValue(columnIndex: int): ValueType--><!--Device-ResultSet-getValue(columnIndex: int): ValueType-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| columnIndex | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 指定的列索引，从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 表示允许的数据字段类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../../apis-basic-services-kit/errorcode-settings.md#14800000-参数检查失败) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指定位置不合法) | ResultSet is empty or pointer index is out of bounds. |
| [14800013](../errorcode-data-rdb.md#14800013-列值为空或列类型与当前调用接口不兼容) | Column index is out of bounds. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch. |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly. |

## goTo

ArkTS-Dyn:
```TypeScript
goTo(offset: number): boolean
```

ArkTS-Sta:
```TypeScript
goTo(offset: int): boolean
```

指定相对当前结果集指针位置的偏移量，以移动结果集的指针位置。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-ResultSet-goTo(offset: int): boolean--><!--Device-ResultSet-goTo(offset: int): boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 表示相对当前结果集指针位置的偏移量，正值表示向后移动，负值表示向前移动。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果成功移动结果集，则为true；否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指定位置不合法) | ResultSet is empty or pointer index is out of bounds. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../../apis-basic-services-kit/errorcode-settings.md#14800000-参数检查失败) | Inner error.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800019](../errorcode-data-rdb.md#14800019-sql必须是查询语句) | The SQL must be a query statement.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |

## goToFirstRow

```TypeScript
goToFirstRow(): boolean
```

转到结果集的第一行。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-ResultSet-goToFirstRow(): boolean--><!--Device-ResultSet-goToFirstRow(): boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果成功移动结果集，则为true；否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指定位置不合法) | ResultSet is empty or pointer index is out of bounds. |
| [14800000](../../apis-basic-services-kit/errorcode-settings.md#14800000-参数检查失败) | Inner error.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800019](../errorcode-data-rdb.md#14800019-sql必须是查询语句) | The SQL must be a query statement.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |

## goToLastRow

```TypeScript
goToLastRow(): boolean
```

转到结果集的最后一行。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-ResultSet-goToLastRow(): boolean--><!--Device-ResultSet-goToLastRow(): boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果成功移动结果集，则为true；否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指定位置不合法) | ResultSet is empty or pointer index is out of bounds. |
| [14800000](../../apis-basic-services-kit/errorcode-settings.md#14800000-参数检查失败) | Inner error.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800019](../errorcode-data-rdb.md#14800019-sql必须是查询语句) | The SQL must be a query statement.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |

## goToNextRow

```TypeScript
goToNextRow(): boolean
```

转到结果集的下一行。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-ResultSet-goToNextRow(): boolean--><!--Device-ResultSet-goToNextRow(): boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果成功移动结果集，则为true；否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指定位置不合法) | ResultSet is empty or pointer index is out of bounds. |
| [14800000](../../apis-basic-services-kit/errorcode-settings.md#14800000-参数检查失败) | Inner error.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800019](../errorcode-data-rdb.md#14800019-sql必须是查询语句) | The SQL must be a query statement.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |

## goToPreviousRow

```TypeScript
goToPreviousRow(): boolean
```

转到结果集的上一行。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-ResultSet-goToPreviousRow(): boolean--><!--Device-ResultSet-goToPreviousRow(): boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果成功移动结果集，则为true；否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指定位置不合法) | ResultSet is empty or pointer index is out of bounds. |
| [14800000](../../apis-basic-services-kit/errorcode-settings.md#14800000-参数检查失败) | Inner error.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800019](../errorcode-data-rdb.md#14800019-sql必须是查询语句) | The SQL must be a query statement.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |

## goToRow

ArkTS-Dyn:
```TypeScript
goToRow(position: number): boolean
```

ArkTS-Sta:
```TypeScript
goToRow(position: int): boolean
```

转到结果集的指定行。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-ResultSet-goToRow(position: int): boolean--><!--Device-ResultSet-goToRow(position: int): boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| position | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 表示要移动到的指定位置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果成功移动结果集，则为true；否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指定位置不合法) | ResultSet is empty or pointer index is out of bounds. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../../apis-basic-services-kit/errorcode-settings.md#14800000-参数检查失败) | Inner error.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800019](../errorcode-data-rdb.md#14800019-sql必须是查询语句) | The SQL must be a query statement.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |

## isColumnNull

ArkTS-Dyn:
```TypeScript
isColumnNull(columnIndex: number): boolean
```

ArkTS-Sta:
```TypeScript
isColumnNull(columnIndex: int): boolean
```

检查当前行中指定列的值是否为null。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-ResultSet-isColumnNull(columnIndex: int): boolean--><!--Device-ResultSet-isColumnNull(columnIndex: int): boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| columnIndex | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 指定的列索引，从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果当前行中指定列的值为null，则返回true，否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800013](../errorcode-data-rdb.md#14800013-列值为空或列类型与当前调用接口不兼容) | Column index is out of bounds. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../../apis-basic-services-kit/errorcode-settings.md#14800000-参数检查失败) | Inner error.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指定位置不合法) | ResultSet is empty or pointer index is out of bounds.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite异步回调请求被中止) | SQLite: Callback routine requested an abort.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite访问权限被拒绝) | SQLite: Access permission denied.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite数据库文件已锁定) | SQLite: The database file is locked.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite数据库中的表被锁定) | SQLite: A table in the database is locked.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite尝试写入只读数据库) | SQLite: Attempt to write a readonly database.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite数据库已满) | SQLite: The database is full.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite由于违反约束而中止) | SQLite: Abort due to constraint violation.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite数据类型不匹配) | SQLite: Data type mismatch.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |
| [14800034](../errorcode-data-rdb.md#14800034-sqlite库使用不正确) | SQLite: Library used incorrectly.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |

## columnCount

```TypeScript
columnCount: int
```

columnCount: int 获取结果集中列的数量。

**类型：** int

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-ResultSet-columnCount: int--><!--Device-ResultSet-columnCount: int-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## columnNames

```TypeScript
columnNames: Array<string>
```

columnNames: Array\&lt;string\&gt; 获取结果集中所有列的名称。当结果集中包含重名列时，获取的列名会不符合预期，建议使用[getColumnNames]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_接口获取。

**类型：** Array&lt;string&gt;

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-ResultSet-columnNames: Array<string>--><!--Device-ResultSet-columnNames: Array<string>-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## isAtFirstRow

```TypeScript
isAtFirstRow: boolean
```

isAtFirstRow: boolean 检查结果集指针是否位于第一行（行索引为0），true表示位于第一行，false表示不位于第一行。

**类型：** boolean

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-ResultSet-isAtFirstRow: boolean--><!--Device-ResultSet-isAtFirstRow: boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## isAtLastRow

```TypeScript
isAtLastRow: boolean
```

isAtLastRow: boolean 检查结果集指针是否位于最后一行，true表示位于最后一行，false表示不位于最后一行。

**类型：** boolean

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-ResultSet-isAtLastRow: boolean--><!--Device-ResultSet-isAtLastRow: boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## isClosed

```TypeScript
isClosed: boolean
```

isClosed: boolean 检查当前结果集是否关闭，true表示结果集已关闭，false表示结果集未关闭。

**类型：** boolean

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-ResultSet-isClosed: boolean--><!--Device-ResultSet-isClosed: boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## isEnded

```TypeScript
isEnded: boolean
```

isEnded: boolean 检查结果集指针是否位于最后一行之后，true表示位于最后一行之后，false表示不位于最后一行之后。

**类型：** boolean

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-ResultSet-isEnded: boolean--><!--Device-ResultSet-isEnded: boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## isStarted

```TypeScript
isStarted: boolean
```

isStarted: boolean 检查指针是否移动过，true表示指针已移动过，false表示指针未移动过。

**类型：** boolean

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-ResultSet-isStarted: boolean--><!--Device-ResultSet-isStarted: boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## rowCount

```TypeScript
rowCount: int
```

rowCount: int 获取结果集中行的数量。

**类型：** int

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-ResultSet-rowCount: int--><!--Device-ResultSet-rowCount: int-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## rowIndex

```TypeScript
rowIndex: int
```

rowIndex: int 获取结果集当前行的索引位置，默认值为-1。索引位置下标从0开始。

**类型：** int

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-ResultSet-rowIndex: int--><!--Device-ResultSet-rowIndex: int-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

