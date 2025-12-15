# ArkData常见问题
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @widecode-->
<!--Designer: @widecode-->
<!--Tester: @logic42-->
<!--Adviser: @ge-yafang-->

## 如何查看关系型数据库详细的SQL语句报错

* 通过调用接口获取。

可以调用[on('sqliteErrorOccurred')](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#onsqliteerroroccurred20)获取SQL执行时出现的异常信息。

## 如何查看关系型数据库执行的SQL语句

* 通过调用接口获取。

可以调用[relationalStore.getInsertSqlInfo](../reference/apis-arkdata/arkts-apis-data-relationalStore-f.md#relationalstoregetinsertsqlinfo20)获取用于插入数据的SQL语句。

可以调用[relationalStore.getUpdateSqlInfo](../reference/apis-arkdata/arkts-apis-data-relationalStore-f.md#relationalstoregetUpdateSqlInfo20)获取用于更新数据的SQL语句。

可以调用[relationalStore.getDeleteSqlInfo](../reference/apis-arkdata/arkts-apis-data-relationalStore-f.md#relationalstoregetDeleteSqlInfo20)获取用于删除数据的SQL语句。

可以调用[relationalStore.getQuerySqlInfo](../reference/apis-arkdata/arkts-apis-data-relationalStore-f.md#relationalstoregetQuerySqlInfo20)获取用于查询数据的SQL语句。