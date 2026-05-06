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

当使用关系型数据时，可能会生成不同的文件产物，不同的文件对应作用具体可见下表。

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
> 以下可搜索的日志在不同版本上可能存在差异。

### 错误码：14800000
**问题场景一：设置分布式表不支持联合主键**

- **问题原因**：

  设置分布式表不支持联合主键，因此调用[setDistributedTables](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#setdistributedtables)等设置分布式表接口会报错14800000。
- **排查步骤**：

  1. 问题时间点附近，搜索日志：`Not support create distributed table with composite primary keys`。

  2. 排查设置分布式表时是否使用了联合主键。
- **建议**：

  设置分布式表时，不要使用联合主键。

**问题场景二：多进程操作数据库，其中一个进程被冻结**
- **问题原因**：

  A进程在操作数据库的过程中退到后台被冻结，数据库锁会被A进程一直持有，此时其他进程调用[getRdbStore](../reference/apis-arkdata/arkts-apis-data-relationalStore-f.md#relationalstoregetrdbstore)等开库接口获取锁会失败，因此报错14800000。
- **排查步骤**：

  1. 搜索进程冻结日志：`Freeze pid: 进程号 success`或者`PID 进程号 has been frozen`。

  2. 正则搜索开库失败日志：`ConnectionPool.*code:-15`。

  3. 搜索进程解冻日志：`Thaw pid: 进程号 success`。

  4. A进程冻结后，其他进程打开数据库失败；A进程解冻后，其他进程打开数据库成功。
- **建议**：

  1. 进程退后台时不要操作数据库，避免并发操作数据库。

  2. 进程退后台时可调用[requestSuspendDelay](../reference/apis-backgroundtasks-kit/js-apis-resourceschedule-backgroundTaskManager.md#backgroundtaskmanagerrequestsuspenddelay)接口申请短时任务，或者调用[startBackgroundRunning](../reference/apis-backgroundtasks-kit/js-apis-resourceschedule-backgroundTaskManager.md#backgroundtaskmanagerstartbackgroundrunning)接口申请长时任务，使得数据库操作在进程被冻结前可以执行结束。

**问题场景三：使用读连接进行写操作**
- **问题原因**：

  读连接不可用于执行写库操作，仅可执行读库操作。
- **排查步骤**：

  排查业务代码，是否存在该操作：调用[beginTransaction](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#begintransaction)接口开启事务之后，在事务未提交的情况下，调用[execute](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#execute12)或者[executeSql](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#executesql)接口依次执行删除触发器a、删除表A、创建表A以及再次删除触发器a的操作。
- **建议**：

  避免在事务未提交的时候，依次执行删除触发器a、删除表A、创建表A以及再次删除触发器a的操作。

**问题场景四：并发查询和删除同一批数据**
- **问题原因**：

  查询时获取到[ResultSet](../reference/apis-arkdata/arkts-apis-data-relationalStore-ResultSet.md)结果集后，删除要查询的部分数据，后续再调用[getLong](../reference/apis-arkdata/arkts-apis-data-relationalStore-ResultSet.md#getlong)等接口获取数据时报错14800000。
- **排查步骤**：

  排查业务代码中，是否存在该操作：获取到结果集后，先调用[execute](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#execute12)、[executeSql](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#executesql)或者[delete](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#delete)接口删除要查询的数据，然后调用[getLong](../reference/apis-arkdata/arkts-apis-data-relationalStore-ResultSet.md#getlong)等接口获取数据。
- **建议**：

  业务需要控制好时序，不要并发查询和删除同一批数据。

**问题场景五：打开加密数据库时，根密钥生成失败**
- **问题原因**：

  huks生成根密钥失败，无法进一步生成加密数据库的密钥，因此调用[getRdbStore](../reference/apis-arkdata/arkts-apis-data-relationalStore-f.md#relationalstoregetrdbstore)等开库接口打开加密数据库失败，报错14800000。
- **排查步骤**：

  业务进程内，正则搜索关键日志：`01650.*Init.*retry.*error`，其中error不为0。
- **建议**：

  重试。

**问题场景六：远程查询时，没有查询到数据**
- **问题原因**：

  在对端数据库中没有要查询的数据的情况下，调用接口[remoteQuery](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#remotequery)进行远程查询，获取到结果集后，调用[goToFirstRow](../reference/apis-arkdata/arkts-apis-data-relationalStore-ResultSet.md#gotofirstrow)等接口获取数据时会报错14800000。
- **排查步骤**：

  确认对端设备的数据库中是否存在要查询的数据。
- **建议**：

  确保要查询的数据存在，再进行远程查询。

**问题场景七：数据服务启动失败，导致设置分布式表失败**
- **问题原因**：

  在数据服务启动失败的情况下，无法设置分布式表，因此调用[setDistributedTables](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#setdistributedtables)等设置分布式表接口会报错14800000。
- **排查步骤**：

  在报错时间点附近，搜索关键日志打印：`Get distributed data manager failed`。
- **建议**：

  重试。

### 错误码：14800011
**问题场景一：打开加密数据库时，密钥不匹配**
- **问题原因**：

  自定义的密钥参数和之前创建加密数据库的密钥参数不匹配。
- **排查步骤**：

  排查自定义密钥参数和之前创建加密数据库的密钥参数是否匹配。
- **建议**：

  每次打开加密数据库时，确保自定义的密钥参数都是一致的。

**问题场景二：数据库文件异常**
- **问题原因**：

  1. 业务进程踩内存，导致数据库文件异常。

  2. 业务进程误关数据库文件的fd，导致数据库文件异常。
- **排查步骤**：

  1. 排查业务进程是否存在踩内存操作。

  2. 排查业务进程是否有误关fd操作。
- **建议**：

  1. 解决业务进程踩内存或者误关fd的问题。

  2. 接入备份恢复。

  3. 删除重建数据库。

### 错误码：14800013
**问题场景：列索引值超过表中字段的数量**
- **问题原因**：

  传入的列索引参数超过表中字段的数量或者为负值，调用[getLong](../reference/apis-arkdata/arkts-apis-data-relationalStore-ResultSet.md#getlong)、[getString](../reference/apis-arkdata/arkts-apis-data-relationalStore-ResultSet.md#getstring)等接口会报错14800013。
- **排查步骤**：

  1. 在业务进程内，正则搜索关键日志：`index.*is out of range|Invalid columnIndex`。

  2. 业务侧需要排查传入参数是否符合预期，是否超过数据库表中的列数。
- **建议**：

  业务需要确保传入参数符合预期，不要超过数据库表中的列数。

### 错误码：14800021
**问题场景一：SQL拼写错误**
- **问题原因**：

  传入的SQL拼写不正确，存在语法问题，SQLite无法识别SQL，调用[executeSql](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#executesql)、[execute](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#execute12)或[executeSync](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#executesync12)等接口执行SQL会报错14800021。
- **排查步骤**：

  1. 在问题时间点附近，正则搜索关键日志：`Error.*unrecognized token|Error.*syntax error|Error.*incomplete input`。

  2. 查看问题时间点附近日志，是否存在上述被匿名的关键日志。
- **建议**：

  1. SQL语句拼写完整。

  2. 触发器中不应该存在`RETURN`关键字。

  3. SQL语句开头不要包含注释。

  4. SQL语句包含`in`时，括号中的匹配值必须传`?`占位符或者具体的值，不要传空值。

  5. SQL中的表名或者字段名附近，不应该存在`{`、`}`或`$`等特殊字符。

**问题场景二：找不到表或者字段**
- **问题原因**：

  数据库中不存在某张表或者表中不存在某个字段，调用[executeSql](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#executesql)、[execute](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#execute12)或[executeSync](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#executesync12)等接口执行SQL会报错14800021。
- **排查步骤**：

  1. 在问题时间点附近，正则搜索关键日志：`Error.*no such table|Error.*no such column`。

  2. 在问题时间点附近，查看建表或添加字段的关键日志：`exe DDL schema`，确认和操作数据库的时序，是否未建表或添加字段就操作数据库。
- **建议**：

  1. 建表或添加字段之后再操作数据库。

  2. 进行加固，重新创建丢失的表或字段。

**问题场景三：重复添加字段**
- **问题原因**：

  重复添加表中已存在的字段，调用[executeSql](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#executesql)、[execute](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#execute12)或[executeSync](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#executesync12)等接口执行SQL会报错14800021。
- **排查步骤**：

  在问题时间点附近，正则搜索关键日志：`Error.*duplicate column name`。
- **建议**：

  不要重复添加表中已存在的字段。

**问题场景四：违反SQLite规格限制**
- **问题原因**：

  违反SQLite规格限制（字符串或BLOB长度超限、列数过多、SQL变量过多、表达式树过深、复合SELECT过多或者附加库过多等），调用[executeSql](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#executesql)、[execute](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#execute12)或[executeSync](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#executesync12)等接口执行SQL会报错14800021。
- **排查步骤**：

  在问题时间点附近，正则搜索关键日志：`too many SQL variables|string or blob too big|too many columns|expression tree too deep|too many terms in compound SELECT|too many attached databases`。
- **建议**：

  确保SQL执行时不违反SQLite规格限制，可参考官方文档：[SQLite系统限制](https://sqlite.org/limits.html)。

**问题场景五：数据库文件异常**
- **问题原因**：

  数据库文件出现异常，导致操作数据库失败，调用[executeSql](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#executesql)、[execute](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#execute12)或[executeSync](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#executesync12)等接口执行SQL会报错14800021。
- **排查步骤**：

  1. 在问题时间点附近，正则搜索关键日志：`Error.*unsupported file format|Error.*database corruption`。

  2. 查看问题时间点附近日志，是否存在上述被匿名的关键日志。

  3. 排查业务进程踩内存或者误关fd的问题。
- **建议**：

  1. 解决业务进程踩内存或者误关fd的问题。

  2. 接入备份恢复。

  3. 删除重建数据库。

### 错误码：14800012
**问题场景一：参考错误码14800021的场景**
- **问题原因**：

  同错误码14800021的各场景原因，调用[getLong](../reference/apis-arkdata/arkts-apis-data-relationalStore-ResultSet.md#getlong)等接口获取数据时会报错14800012。
- **排查步骤**：

  同错误码14800021的各场景排查步骤。
- **建议**：

  同错误码14800021的各场景建议。

**问题场景二：查询的单条数据大小超过2M**
- **问题原因**：

  查询时获取到[ResultSet](../reference/apis-arkdata/arkts-apis-data-relationalStore-ResultSet.md)结果集，由于共享内存大小为2M，因此当单条数据大小超过2M时，调用[goToFirstRow](../reference/apis-arkdata/arkts-apis-data-relationalStore-ResultSet.md#gotofirstrow)、[goToNextRow](../reference/apis-arkdata/arkts-apis-data-relationalStore-ResultSet.md#gotonextrow)等接口填充共享内存会失败，此时调用[getLong](../reference/apis-arkdata/arkts-apis-data-relationalStore-ResultSet.md#getlong)等接口获取数据会报错14800012。
- **排查步骤**：

  1. 在业务进程中，正则搜索关键日志：`ResetStatement.*over 2MB`。

  2. 排查单条数据大小是否超过2M。
- **建议**：

  建议调用[queryWithoutRowCount](../reference/apis-arkdata/arkts-apis-data-relationalStore-RdbStore.md#querywithoutrowcount23)接口获取结果集[LiteResultSet](../reference/apis-arkdata/arkts-apis-data-relationalStore-LiteResultSet.md)后，再查询单条大小超过2M的数据。

**问题场景三：表中无数据或者无符合查询条件的数据**
- **问题原因**：

  当表中无数据或者无符合查询条件的数据时，调用[getLong](../reference/apis-arkdata/arkts-apis-data-relationalStore-ResultSet.md#getlong)等接口获取数据会报错14800012。
- **排查步骤**：

  1. 排查表中是否存在数据。

  2. 排查表中是否存在符合查询条件的数据。
- **建议**：

  1. 插入数据后再查询。

  2. 查询条件要符合预期，确保可以查询到数据。