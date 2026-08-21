# ArkData常见问题
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @htt1997-->
<!--Tester: @logic42-->
<!--Adviser: @ge-yafang-->

## 如何查看关系型数据库详细的SQL执行异常信息

可以调用[on('sqliteErrorOccurred')](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#onsqliteerroroccurred20)获取SQL执行时出现的异常信息。

## 如何查看关系型数据库生成的SQL语句

可以调用[relationalStore.getInsertSqlInfo](../reference/apis-arkdata/arkts-apis-data-relationalStore-f.md#relationalstoregetinsertsqlinfo20)获取用于插入数据的SQL语句。

可以调用[relationalStore.getUpdateSqlInfo](../reference/apis-arkdata/arkts-apis-data-relationalStore-f.md#relationalstoregetupdatesqlinfo20)获取用于更新数据的SQL语句。

可以调用[relationalStore.getDeleteSqlInfo](../reference/apis-arkdata/arkts-apis-data-relationalStore-f.md#relationalstoregetdeletesqlinfo20)获取用于删除数据的SQL语句。

可以调用[relationalStore.getQuerySqlInfo](../reference/apis-arkdata/arkts-apis-data-relationalStore-f.md#relationalstoregetquerysqlinfo20)获取用于查询数据的SQL语句。

## 关系型数据库不同文件说明

当使用关系型数据库时，可能会生成不同的文件产物，不同的文件对应作用具体可见下表。

| **文件类型** | **说明**                                                             |
| ------------ | ----------------------------------------------------------------------- |
| .db          | 数据库持久化文件，用于存储数据库数据。                                               |
| .db-wal     | 用于保存操作日志，可以在事务失败时回滚更改，确保数据一致性。<br>该文件仅在数据库采用WAL模式时存在（系统默认日志方式即为WAL（Write Ahead Log）模式）。  |
| .db-shm      | 共享内存文件，用于协调多个数据库连接对同一db文件的更改，防止数据冲突。<br>该文件仅在数据库采用WAL模式时存在（系统默认日志方式即为WAL（Write Ahead Log）模式）。                   |
| .key_lock      | 用于保存文件锁信息。                            |
| .pub_key     | 用于保存数据库密钥信息。<br>该文件仅在配置了数据库加密且未配置自定义加密参数时（即通过[StoreConfig](../reference/apis-arkdata/arkts-apis-data-relationalStore-i.md#storeconfig)配置encrypt为true且未配置cryptoParam）存在。                                                  |
| .db-dwr      | 用于保存文件头信息。                                       |
| .db-compare      | 用于保存所有DDL语句。                                    |

## 调用getRdbStore接口使用原始密钥打开加密关系型数据库时，入参encryptionKey如何配置

在关系型数据库中，调用[getRdbStore](../reference/apis-arkdata/arkts-apis-data-relationalStore-f.md#relationalstoregetrdbstore)接口使用原始密钥打开加密库时，入参[CryptoParam.encryptionKey](../reference/apis-arkdata/arkts-apis-data-relationalStore-i.md#cryptoparam14)需要按照如下操作配置：

```ts
import { relationalStore } from '@kit.ArkData'

let password: string = "x'3605d7de19311edba4d3c88143c61cdd79dd5a58bc829c8b1234567891234567'"; // 需替换为实际的数据库口令密码
let key = new Uint8Array(buffer.from(password, 'utf8').buffer); // 返回的是Uint8Array
// 配置加密参数
const cryptoParam: relationalStore.CryptoParam = {
  encryptionKey: key, // 必填，指定密钥
};
```