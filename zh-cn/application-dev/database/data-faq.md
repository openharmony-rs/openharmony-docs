# ArkData常见问题
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @widecode-->
<!--Designer: @widecode-->
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


## 关系型数据库错误码常见场景及排查步骤
> **说明：**
>
> 以下错误码可参考：[关系型数据库错误码](../reference/apis-arkdata/errorcode-data-rdb.md)。
>
> 获取hilog系统日志的方法可参考：[hilog日志查看](../dfx/hilog.md#hilog日志查看)。
>
> 以下可搜索的日志在不同版本上可能存在差异。

### 错误码：14800000

**可能原因：**
- 设置分布式表不支持联合主键，因此调用[setDistributedTables](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#setdistributedtables)等设置分布式表接口会失败。
- 多进程操作数据库，其中一个进程被冻结，数据库锁会被当前冻结进程一直持有，直到解冻才会释放，在此期间其他进程调用[getRdbStore](../reference/apis-arkdata/arkts-apis-data-relationalStore-f.md#relationalstoregetrdbstore)等接口开库时获取锁会失败。
- 使用读连接进行写操作。读连接不可用于执行写库操作，仅可执行读库操作。
- 并发查询和删除同一批数据。
- 根密钥生成失败。huks生成根密钥失败，无法进一步生成加密数据库的密钥，因此调用[getRdbStore](../reference/apis-arkdata/arkts-apis-data-relationalStore-f.md#relationalstoregetrdbstore)等开库接口打开加密数据库会失败。
- 远程查询时，没有查询到数据。在对端数据库中不存在要查询的数据的情况下，调用[remoteQuery](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#remotequery)接口进行远程查询，获取到结果集后，再调用[goToFirstRow](../reference/apis-arkdata/arkts-apis-data-relationalStore-ResultSet.md#gotofirstrow)等接口获取数据会失败。
- 数据管理服务启动失败。在数据管理服务启动失败的情况下，无法设置分布式表，因此调用[setDistributedTables](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#setdistributedtables)等设置分布式表接口会失败。

**处理步骤：**
1. 确认问题时间点附近，是否存在该日志打印：`Not support create distributed table with composite primary keys`。
   - 是：设置分布式表时不要使用联合主键。
   - 否：转下一步。
2. 确认问题时间点附近，是否可正则搜索到和进程冻结相关的日志：`Freeze pid: 进程号 success`或`PID 进程号 has been frozen`，以及开库失败的日志：`ConnectionPool.*code:-15`。
   - 是：进程退后台时不要操作数据库，避免多进程并发操作数据库；调用[requestSuspendDelay](../reference/apis-backgroundtasks-kit/js-apis-resourceschedule-backgroundTaskManager.md#backgroundtaskmanagerrequestsuspenddelay)接口申请短时任务或调用[startBackgroundRunning](../reference/apis-backgroundtasks-kit/js-apis-resourceschedule-backgroundTaskManager.md#backgroundtaskmanagerstartbackgroundrunning)接口申请长时任务，使得数据库操作在进程被冻结前可以执行结束。
   - 否：转下一步。
3. 排查业务代码是否存在如下操作：调用[beginTransaction](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#begintransaction)接口开启事务后，事务未提交时，调用[execute](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#execute12)或者[executeSql](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#executesql)接口依次执行：删除触发器a、删除表A、重建表A，后续再次删除触发器a时出现失败。
   - 是：避免在事务未提交的时候，依次执行删除触发器a、删除表A、重建表A以及再次删除触发器a的类似操作。
   - 否：转下一步。
4. 排查业务代码是否存在如下操作：获取结果集后，先调用[execute](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#execute12)、[executeSql](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#executesql)或[delete](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#delete)接口删除待查询的数据，再调用[getLong](../reference/apis-arkdata/arkts-apis-data-relationalStore-ResultSet.md#getlong)等接口获取数据时出现失败。
   - 是：业务需要控制好时序，不要并发查询和删除同一批数据。
   - 否：转下一步。
5. 确认问题时间点附近，是否可正则搜索到关键日志：`01650.*Init.*retry.*error`，其中error不为0。
   - 是：根密钥可能生成失败，业务需要重试打开加密数据库。
   - 否：转下一步。
6. 确认对端设备的数据库中是否存在要查询的数据。
   - 是：转下一步。
   - 否：确保要查询的数据存在，再进行远程查询。
7. 确认问题时间点附近，是否可搜索到关键日志：`Get distributed data manager failed`。
   - 是：数据管理服务启动失败，业务需要重试设置分布式表。
   - 否：提供hilog系统日志，联系技术支撑人员定位。

### 错误码：14800011

**可能原因：**
- 打开加密数据库时，自定义密钥不匹配，因此调用[getRdbStore](../reference/apis-arkdata/arkts-apis-data-relationalStore-f.md#relationalstoregetrdbstore)等接口开库时会失败。
- 数据库文件异常，因此调用增删改查等接口操作数据库会失败。

**处理步骤：**
1. 排查自定义密钥参数和之前创建加密数据库的密钥参数是否一致。
   - 是：转下一步。
   - 否：每次打开加密数据库时，确保自定义的密钥参数都是一致的。
2. 确认是否可以参考[数据库文件异常](../reference/apis-arkdata/errorcode-data-rdb.md#14800011-数据库文件异常)的处理步骤解决问题。
   - 是：参考数据库文件异常的处理步骤。
   - 否：提供hilog系统日志，联系技术支撑人员定位。

### 错误码：14800013

**可能原因：** 传入的列索引参数超过表中字段的数量或者为负值，因此调用[getLong](../reference/apis-arkdata/arkts-apis-data-relationalStore-ResultSet.md#getlong)、[getString](../reference/apis-arkdata/arkts-apis-data-relationalStore-ResultSet.md#getstring)等接口会失败。

**处理步骤：** 确认问题时间点附近，是否可正则搜索到关键日志：`index.*is out of range|Invalid columnIndex`，同时排查传入的列索引参数是否超过表中字段的数量或者为负值。
   - 是：确保传入参数符合预期，不要超过数据库表中的列数。
   - 否：提供hilog系统日志，联系技术支撑人员定位。

### 错误码：14800021

**可能原因：**
- SQL拼写错误，存在语法问题，调用[executeSql](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#executesql)、[execute](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#execute12)或[executeSync](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#executesync12)等接口执行SQL会失败。
- 数据库中不存在某张表或者表中不存在某个字段，调用[executeSql](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#executesql)、[execute](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#execute12)或[executeSync](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#executesync12)等接口执行SQL会失败。
- 重复添加表中已存在的字段，调用[executeSql](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#executesql)、[execute](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#execute12)或[executeSync](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#executesync12)等接口执行SQL会失败。
- 违反SQLite系统限制（字符串或BLOB长度超限、列数过多、SQL变量过多、表达式树过深、复合SELECT过多或附加库过多等），调用[executeSql](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#executesql)、[execute](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#execute12)或[executeSync](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#executesync12)等接口执行SQL会失败。
- 数据库文件异常，调用[executeSql](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#executesql)、[execute](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#execute12)或[executeSync](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#executesync12)等接口执行SQL会失败。

**处理步骤：**
1. 确认问题时间点附近，是否可正则搜索到关键日志：`Error.*unrecognized token|Error.*syntax error|Error.*incomplete input`。
   - 是：SQL语句需要拼写完整；触发器语句中不要存在`RETURN`关键字；SQL语句开头不要包含注释；SQL语句包含`in`时，括号中的匹配值必须传`?`占位符或者具体的值，不要传空值；SQL中的表名或字段名附近，不要存在`{`、`}`或`$`等特殊字符。
   - 否：转下一步。
2. 确认问题时间点附近，是否可正则搜索到关键日志：`Error.*no such table|Error.*no such column`。
   - 是：建表或添加字段之后再操作数据库；进行加固，重新创建丢失的表或添加字段。
   - 否：转下一步。
3. 确认问题时间点附近，是否可正则搜索到关键日志：`Error.*duplicate column name`。
   - 是：不要重复添加表中已存在的字段。
   - 否：转下一步。
4. 确认问题时间点附近，是否可正则搜索到关键日志：`too many SQL variables|string or blob too big|too many columns|expression tree too deep|too many terms in compound SELECT|too many attached databases`。
   - 是：确保SQL执行时不违反SQLite系统限制，可参考官方文档：[SQLite系统限制](https://sqlite.org/limits.html)。
   - 否：转下一步。
5. 确认问题时间点附近，是否可正则搜索到关键日志：`Error.*unsupported file format|Error.*database corruption`。
   - 是：解决业务进程踩内存或误关fd的问题；接入备份恢复；删除重建数据库。
   - 否：提供hilog系统日志，联系技术支撑人员定位。

### 错误码：14800012

**可能原因：**
- SQL拼写错误、找不到表或字段、重复添加字段、违反SQLite系统限制、数据库文件异常等（参考错误码14800021的问题场景），调用[getLong](../reference/apis-arkdata/arkts-apis-data-relationalStore-ResultSet.md#getlong)等接口获取数据时会失败。
- 查询的单条数据大小超过2M，调用[getLong](../reference/apis-arkdata/arkts-apis-data-relationalStore-ResultSet.md#getlong)等接口获取数据时会失败。
- 表中无任何数据，调用[getLong](../reference/apis-arkdata/arkts-apis-data-relationalStore-ResultSet.md#getlong)等接口获取数据时会失败。
- 表中无符合查询条件的数据，调用[getLong](../reference/apis-arkdata/arkts-apis-data-relationalStore-ResultSet.md#getlong)等接口获取数据时会失败。

**处理步骤：**
1. 确认是否可以参考错误码14800021的处理步骤排查到问题。
   - 是：参考错误码14800021的处理步骤。
   - 否：转下一步。
2. 确认问题时间点附近，是否可正则搜索到关键日志：`ResetStatement.*over 2MB`或者排查单条数据的大小是否超过2M。
   - 是：调用[queryWithoutRowCount](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#querywithoutrowcount23)接口获取结果集[LiteResultSet](../reference/apis-arkdata/arkts-apis-data-relationalStore-LiteResultSet.md)后，再查询单条大小超过2M的数据。
   - 否：转下一步。
3. 排查表中是否存在数据。
   - 是：转下一步。
   - 否：插入数据后再查询。
4. 排查表中是否存在符合查询条件的数据。
   - 是：提供hilog系统日志，联系技术支撑人员定位。
   - 否：确保查询条件符合预期，可以查询到数据。