# 关系型数据库错误码
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @widecode; @htt1997-->
<!--Tester: @yippo; @logic42-->
<!--Adviser: @ge-yafang-->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

##  14800000 内部错误

**错误信息**

Inner error.

**错误描述**

内部错误。

**可能原因**

优先查看错误日志，通过日志可以详细了解错误原因，主要有以下几种：
1. sql执行异常。
2. 内部状态异常。
3. 错误地使用接口。
4. 系统错误，如空指针、内存不足、数据服务异常重启、I/O错误、IPC异常、JS引擎异常等。

**处理步骤**

1. 开发者排查sql语句和谓词是否正确使用。
2. 开发者排查是否存在对象关闭后再使用。
3. 开发者排查是否按接口文档正确使用接口。
4. 尝试重试，如果依然无法解决，可以提示用户重启应用、升级应用或升级设备版本。

##  14800001 无效的参数

**错误信息**

Invalid arguments. Possible causes: 1. Parameter is out of valid range; 2. Missing GROUP BY clause.

**错误描述**

无效的参数。

**可能原因**

入参不符合接口要求，如取值范围、长度、格式等。

**处理步骤**

参考接口参数说明修改参数符合要求。

## 14800010 数据库路径不合法

**错误信息**

Failed to open or delete the database by an invalid database path.

**错误描述**

数据库路径不合法，打开或删除数据库失败。

**可能原因**

无效的数据库路径。

**处理步骤**

检查传入数据库路径。

## 14800011 数据库文件异常

**错误信息**

Failed to open the database because it is corrupted.

**错误描述**

数据库异常，打开失败。

**可能原因**

数据库文件不完整、数据库fd被误操作、数据库内存被踩等。

**处理步骤**

如果可以接受数据库数据丢失，则可尝试删除数据库后重新创建。否则，需要备份数据库以便恢复。具体操作可参考[数据库备份与恢复](../../database/data-backup-and-restore.md)。

## 14800012 结果集为空或指定位置不合法

**错误信息**

ResultSet is empty or pointer index is out of bounds.

**错误描述**

结果集为空或指定位置不合法。

**可能原因**

结果集为空或结果集指定行号超出位置范围[0, m - 1]，m = resultsetV9.rowCount。

**处理步骤**

检查当前操作得到的结果集是否为空或指定的位置是否合法。

## 14800013 列值为空或列类型与当前调用接口不兼容

**错误信息**

ResultSet is empty or column index is out of bounds.

**错误描述**

列值为空或列类型与当前调用接口不兼容。

**可能原因**

1. 结果集为空。
2. 结果集当前行号超出范围[0, m - 1]，m = resultsetV9.rowCount。
3. 当前列号超出范围[0, n - 1]，n = resultsetV9.columnCount。
4. 当前列数据类型接口不支持。

**处理步骤**

1. 检查结果集是否为空。
2. 检查结果集当前行号、列号是否超出范围。
3. 检查当前列数据类型是否支持。

## 14800014 数据库或结果集关闭

**错误信息**

The RdbStore or ResultSet is already closed.

**错误描述**

数据库或结果集关闭。

**可能原因**

RdbStore或者ResultSet等带有close接口的对象，已调用过close或者没有打开成功。

**处理步骤**

重新打开RdbStore或者重新查询获取得到ResultSet。

## 14800015 数据库没有响应

**错误信息**

The database does not respond.

**错误描述**

数据库没有响应。

**可能原因**

有读、写、attach、detach等操作正在执行，无法在指定的时间（默认2s）内执行当前操作。

**处理步骤**

1. 重新尝试。
2. 如果是[attach](arkts-apis-data-relationalStore-RdbStore.md#attach12)或[detach](arkts-apis-data-relationalStore-RdbStore.md#detach12)接口，增加waitTime值来增加等待时长。

## 14800016 数据库别名已被使用

**错误信息**

The database alias already exists.

**错误描述**

附加后的数据库别名已被使用。

**可能原因**

附加后的数据库的别名已被使用。

**处理步骤**

不进行附加数据库操作或者修改附加后数据库的别名。

## 14800017 关键配置已被更改

**错误信息**

StoreConfig is changed.

**错误描述**

数据库关键配置已被更改。

**可能原因**

数据库的area（区域），securityLevel（安全级别），数据库读写权限等关键配置发生变化。

**处理步骤**

保持原配置不变或者用原配置导出数据，删除旧库，用新配置创建新库，数据存入新库。
检查是否使用chmod修改了数据库文件的读写权限，确保当前用户有足够的权限来读写数据库文件。

## 14800018 查询结果没有数据符合条件

**错误信息**

No data meets the condition.

**错误描述**

SQL语句有误，未查询到符合条件的数据。

**可能原因**

没有编写查询正确结果集的SQL语句。

**处理步骤**

编写正确的查询语句或者添加数据库数据之后再做查询。

## 14800019 SQL必须是查询语句

**错误信息**

The SQL must be a query statement.

**错误描述**

SQL必须是查询语句。

**可能原因**

SQL语句不符合规定，导致查询失败。

**处理步骤**

SQL语句不符合规定导致执行失败时，编写满足规约的SQL语句。

## 14800020 密钥损坏或丢失

**错误信息**

The secret key is corrupted or lost.

**错误描述**

获取密钥失败。

**可能原因**

根密钥丢失、无权限读取密钥文件、密钥文件损坏等。

**处理步骤**

1. 检查密钥文件权限、内容是否正常。
2. 重建或restore恢复数据库。

## 14800021 SQLite：通用错误

**错误信息**

SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist.

**错误描述**

SQLite：通用错误。

**可能原因**

执行sql语句过程中出现错误，如：
1. 插入或更新未创建的表。
2. 插入或更新未曾有的列。
3. 调用未定义的函数等，参见SQLITE_ERROR的相关错误场景。

**处理步骤**

开发者分析错误的SQL语句，找出错误点。

## 14800022 SQLite：异步回调请求被中止

**错误信息**

SQLite: Callback routine requested an abort.

**错误描述**

SQLite：异步回调请求被中止。

**可能原因**

1. 通常发生在使用SQLite的自定义函数机制时，回调被中止执行。
2. 参见SQLITE_ABORT的相关错误场景。

**处理步骤**

检查SQLite的钩子函数（callback）的实现，确保其正确性。

## 14800023 SQLite：访问权限被拒绝

**错误信息**

SQLite: Access permission denied.

**错误描述**

SQLite访问权限被拒绝。

**可能原因**

1. 操作系统级别的权限问题，意味着SQLite试图访问或修改一个文件，但是没有足够的权限去执行这个操作。
2. 参见SQLITE_PERM的相关错误场景。

**处理步骤**

1. 确认文件没有只读属性，如果有，去掉只读属性。
2. 检查文件和文件夹的权限，确保当前用户有足够的权限来读写文件。
3. 检查文件系统是否为只读，如果是，改为可写状态。
4. 确认没有其他进程锁定数据库文件，如果有，关闭占用文件的进程。
5. 在处理权限问题时，确保有足够的权限去更改相关的文件或文件夹权限。

## 14800024 SQLite：数据库文件已锁定

**错误信息**

SQLite: The database file is locked.

**错误描述**

SQLite数据库文件已锁定。

**可能原因**

1. 同一应用两个进程，例如UIability和datashareability同时打开了同一个数据库，进行增删改操作，或者不同应用的同一个group组内的进程通过group组打开同一个数据库，进行增删改操作。
2. 参见SQLITE_BUSY的相关错误场景。

**处理步骤**

1. 避免进程并发操作数据库。
2. 等待一段时间重试。

## 14800025 SQLite：数据库中的表被锁定

**错误信息**

SQLite: A table in the database is locked.

**错误描述**

SQLite：数据库中的表被锁定。

**可能原因**

1. 在尝试写入SQLite数据库时，但数据库文件已被另一个进程锁定。这可能是因为数据库处于事务中，或者有其他的锁机制在阻止写入。
2. 参见SQLITE_LOCKED的相关错误场景。

**处理步骤**

1. 确保没有其他进程或线程正在对数据库文件进行写操作。
2. 如果使用了事务，请确保在开始事务后及提交事务前不要进行任何写操作。
3. 检查是否有其他锁机制（如文件锁）可能阻止了写入。
4. 如果数据库连接对象没有正确关闭，确保在完成数据库操作后关闭连接。
5. 如果在多线程环境中，确保对数据库操作加锁，防止竞争条件。

## 14800026 SQLite：数据库内存不足

**错误信息**

SQLite: The database is out of memory.

**错误描述**

SQLite：数据库内存不足。

**可能原因**

数据库内存不足，可能是由于数据量过大或内存分配不足导致的。

**处理步骤**

减小数据量或增加内存分配。

## 14800027 SQLite：尝试写入只读数据库

**错误信息**

SQLite: Attempt to write a readonly database.

**错误描述**

SQLite：尝试写入只读数据库。

**可能原因**

1. 尝试写入一个以只读模式打开的SQLite数据库文件时。这可能是因为文件权限问题，文件处于只读文件系统中或者数据库被标记为只读。
2. 参见SQLITE_READONLY的相关错误场景。

**处理步骤**

1. 确保有足够的权限去写入数据库文件。
2. 如果文件系统是只读的，需要将其改为读写模式。
3. 确认在打开数据库时没有使用只读模式参数。

## 14800028 SQLite：发生了某种磁盘I/O错误

**错误信息**

SQLite: Some kind of disk I/O error occurred.

**错误描述**

SQLite发生了某种磁盘I/O错误。

**可能原因**

可能是由于多种原因造成的，包括但不限于：
1. 文件不存在。
2. 文件是只读的。
3. 磁盘空间不足。
4. 文件损坏。
5. 参见SQLITE_IOERR的相关错误场景。

**处理步骤**

1. 检查文件路径是否正确，文件是否存在。
2. 确保文件没有设置为只读。
3. 检查磁盘空间是否足够，并清理不必要的文件释放空间。
4. 检查文件的权限，确保应用程序有足够的权限去读写文件。

## 14800029 SQLite：数据库已满

**错误信息**

SQLite: The database is full.

**错误描述**

SQLite数据库已满。

**可能原因**

数据库已满，可能是由于数据量过大或磁盘空间不足导致的。

**处理步骤**

减小数据量或增加磁盘空间。

## 14800030 SQLite：无法打开数据库文件

**错误信息**

SQLite: Unable to open the database file.

**错误描述**

SQLite：无法打开数据库文件。

**可能原因**

1. 文件不存在，并且创建新数据库失败。
2. 文件存在，但是数据库文件损坏。
3. 文件权限问题，SQLite无法读写文件。
4. 磁盘空间不足。
5. 参见SQLITE_CANTOPEN的相关错误场景。

**处理步骤**

1. 确认数据库文件路径是否正确，检查文件权限，确保应用程序有足够的权限去读写文件。
2. 确认磁盘空间足够。

## 14800031 SQLite：TEXT或BLOB超出大小限制

**错误信息**

SQLite: TEXT or BLOB exceeds size limit.

**错误描述**

SQLite：TEXT或BLOB超出大小限制。

**可能原因**

1. 查询的结果集超过了SQLite所能处理的大小限制。
2. 参见SQLITE_TOOBIG的相关错误场景。

**处理步骤**

将大查询分解为多个小查询，每次处理一部分数据。

## 14800032 SQLite：由于违反约束而中止

**错误信息**

SQLite: Abort due to constraint violation.

**错误描述**

SQLite：由于违反约束而中止。

**可能原因**

1. 尝试写入SQLite数据库时违反了数据库的完整性约束条件。
2. 参见SQLITE_CONSTRAINT的相关错误场景。

**处理步骤**

检查试图插入或更新的数据是否违反了上述约束。

## 14800033 SQLite：数据类型不匹配

**错误信息**

SQLite: Data type mismatch.

**错误描述**

SQLite：数据类型不匹配。

**可能原因**

1. 执行一个SQL语句时，其中涉及的数据类型与数据库中存储的数据类型不匹配。
2. 参见SQLITE_MISMATCH的相关错误场景。

**处理步骤**

检查SQL语句中涉及的列的数据类型，确保插入、更新或查询的数据类型与列的数据类型相匹配。

## 14800034 SQLite：库使用不正确

**错误信息**

SQLite: Library used incorrectly.

**错误描述**

SQLite：库使用不正确。

**可能原因**

1. 表示数据库操作或者使用上下文不正确。这个错误通常发生在以下几种情况：
    - 数据库还没有完成操作就进行下一个操作。
    - 在一个数据库连接已经关闭后，继续对该连接进行操作。
    - 使用了已经释放或无效的数据库对象。
2. 参见SQLITE_MISUSE的相关错误场景。

**处理步骤**

1. 确保数据库操作之间有适当的同步，比如使用锁或其他同步机制。
2. 确保数据库连接在使用前是打开的，在结束操作后是关闭的。
3. 确保所有数据库对象在使用完毕后都已正确释放。

## 14800047 WAL文件大小超过默认上限

**错误信息**

The WAL file size exceeds the default limit.

**错误描述**

WAL文件大小超过默认上限（512MB）。

**可能原因**

在开启读事务或者结果集未关闭的情况下，不断执行增删改操作，导致WAL文件大小超过默认上限。

**处理步骤**

检查结果集或者事务是否未关闭。

关闭所有的结果集或者事务。

## 14800050 获取订阅服务失败

**错误信息**

Failed to obtain the subscription service.

**错误描述**

获取订阅服务失败。

**可能原因**

当前平台不支持订阅服务。

**处理步骤**

需要在当前平台部署订阅服务。

## 14801001 上下文环境非Stage模型

**错误信息**

The operation is supported in the stage model only.

**错误描述**

该操作仅支持Stage模型。

**可能原因**

当前上下文环境非Stage模型。

**处理步骤**

切换当前上下文环境，使用Stage模型。

## 14801002 storeConfig中传入的dataGroupId参数非法

**错误信息**

Invalid data group ID.

**错误描述**

使用非法dataGroupId参数。

**可能原因**

使用的dataGroupId不是从应用市场正常申请的。

**处理步骤**

从应用市场申请dataGroupId，并正确传入该参数。

## 14800051 分布式表类型不匹配

**错误信息**

The type of the distributed table does not match.

**错误描述**

对同一数据库表设置的分布式表类型前后不一致。

**可能原因**

对同一数据库表设置的分布式表类型前后不一致，分布式表类型可见[DistributedType](arkts-apis-data-relationalStore-e.md#distributedtype10)。

**处理步骤**

对同一数据库表设置的分布式表类型保持一致，属于端端同步的分布式表不可再设置为用于端云的同步表。