# deleteRdbStore

## 导入模块

```TypeScript
import { relationalStore } from '@kit.ArkData';
```

## deleteRdbStore

```TypeScript
function deleteRdbStore(context: Context, name: string, callback: AsyncCallback<void>): void
```

删除数据库文件，使用callback异步回调。

删除成功后，建议将数据库对象置为null。建立数据库时，若在[StoreConfig](arkts-arkdata-relationalstore-storeconfig-i.md)中配置了自定义路径，则调用此接口进行删库无效，必须使用[deleteRdbStore](arkts-arkdata-relationalstore-deleterdbstore-f.md) 接口进行删库。

当使用向量数据库时，在调用deleteRdbStore接口前，应当确保向量数据库已打开的RdbStore和ResultSet均已成功关闭。

**起始版本：** 9

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | 应用的上下文。<br>FA模型的应用Context定义见Context。<br>Stage模型的应用Context定义见Context。 |
| name | string | 是 | 数据库名称，不能为空字符串且不能包含路径分隔符/。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当删除数据库成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800010](../errorcode-data-rdb.md#14800010-数据库路径不合法) | Failed to open or delete the database by an invalid database path. |

**示例**

```TypeScript
FA模型示例：
```

```TypeScript
Stage模型示例：
```


## deleteRdbStore

```TypeScript
function deleteRdbStore(context: Context, config: StoreConfig, callback: AsyncCallback<void>): void
```

使用指定的数据库文件配置删除数据库，使用callback异步回调。

删除成功后，建议将数据库对象置为null。若数据库文件处于公共沙箱目录下，则删除数据库时必须使用该接口，当存在多个进程操作同一个数据库的情况，建议向其他进程发送数据库删除通知使其感知并处理。建立数据库时，若在[StoreConfig](arkts-arkdata-relationalstore-storeconfig-i.md)中配置了自定义路径，则必须调用此接口进行删库。

当使用向量数据库时，在调用deleteRdbStore接口前，应当确保向量数据库已打开的RdbStore和ResultSet均已成功关闭。

**起始版本：** 10

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | 应用的上下文。<br>FA模型的应用Context定义见Context。<br>Stage模型的应用Context定义见Context。 |
| config | [StoreConfig](arkts-arkdata-relationalstore-storeconfig-i.md) | 是 | 与此RDB存储相关的数据库配置。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当删除数据库成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800010](../errorcode-data-rdb.md#14800010-数据库路径不合法) | Failed to open or delete the database by an invalid database path. |
| [14801001](../errorcode-data-rdb.md#14801001-上下文环境非stage模型) | The operation is supported in the stage model only. |
| [14801002](../errorcode-data-rdb.md#14801002-storeconfig中传入的datagroupid参数非法) | Invalid data group ID. |

**示例**

参见 [deleteRdbStore](#deleterdbstore)


## deleteRdbStore

```TypeScript
function deleteRdbStore(context: Context, name: string): Promise<void>
```

删除数据库文件，使用Promise异步回调。

删除成功后，建议将数据库对象置为null。建立数据库时，若在[StoreConfig](arkts-arkdata-relationalstore-storeconfig-i.md)中配置了自定义路径，则调用此接口进行删库无效，必须使用[deleteRdbStore](arkts-arkdata-relationalstore-deleterdbstore-f.md) 接口进行删库。

当使用向量数据库时，在调用deleteRdbStore接口前，应当确保向量数据库已打开的RdbStore和ResultSet均已成功关闭。

**起始版本：** 9

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | 应用的上下文。<br>FA模型的应用Context定义见Context。<br>Stage模型的应用Context定义见Context。 |
| name | string | 是 | 数据库名称，不能为空字符串且不能包含路径分隔符/。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800010](../errorcode-data-rdb.md#14800010-数据库路径不合法) | Failed to open or delete the database by an invalid database path. |

**示例**

参见 [deleteRdbStore](#deleterdbstore)


## deleteRdbStore

```TypeScript
function deleteRdbStore(context: Context, config: StoreConfig): Promise<void>
```

使用指定的数据库文件配置删除数据库，使用Promise异步回调。

删除成功后，建议将数据库对象置为null。若数据库文件处于公共沙箱目录下，则删除数据库时必须使用该接口，当存在多个进程操作同一个数据库的情况，建议向其他进程发送数据库删除通知使其感知并处理。建立数据库时，若在[StoreConfig](arkts-arkdata-relationalstore-storeconfig-i.md)中配置了自定义路径，则必须调用此接口进行删库。

当使用向量数据库时，在调用deleteRdbStore接口前，应当确保向量数据库已打开的RdbStore和ResultSet均已成功关闭。

**起始版本：** 10

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | 应用的上下文。<br>FA模型的应用Context定义见Context。<br>Stage模型的应用Context定义见Context。 |
| config | [StoreConfig](arkts-arkdata-relationalstore-storeconfig-i.md) | 是 | 与此RDB存储相关的数据库配置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-内部错误) | Inner error. |
| [14800010](../errorcode-data-rdb.md#14800010-数据库路径不合法) | Failed to open or delete the database by an invalid database path. |
| [14801001](../errorcode-data-rdb.md#14801001-上下文环境非stage模型) | The operation is supported in the stage model only. |
| [14801002](../errorcode-data-rdb.md#14801002-storeconfig中传入的datagroupid参数非法) | Invalid data group ID. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported.<br>**适用版本：** 12+ |

**示例**

参见 [deleteRdbStore](#deleterdbstore)
