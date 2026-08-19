# deleteRdbStore

## 导入模块

```TypeScript
```

## deleteRdbStore

```TypeScript
function deleteRdbStore(context: Context, name: string, callback: AsyncCallback<void>): void
```

删除数据库，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [deleteRdbStore](arkts-arkdata-relationalstore-deleterdbstore-f.md)

<!--Device-rdb-function deleteRdbStore(context: Context, name: string, callback: AsyncCallback<void>): void--><!--Device-rdb-function deleteRdbStore(context: Context, name: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | 应用的上下文。 <br>FA模型的应用Context定义见Context。 <br>Stage模型的应用Context定义见Context。 |
| name | string | 是 | 数据库名称，不能为空字符串且不能包含路径分隔符/。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当操作成功，err为undefined；否则为错误对象。 |


## deleteRdbStore

```TypeScript
function deleteRdbStore(context: Context, name: string): Promise<void>
```

使用指定的数据库文件配置删除数据库，使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [deleteRdbStore](arkts-arkdata-relationalstore-deleterdbstore-f.md)

<!--Device-rdb-function deleteRdbStore(context: Context, name: string): Promise<void>--><!--Device-rdb-function deleteRdbStore(context: Context, name: string): Promise<void>-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | 应用的上下文。 <br>FA模型的应用Context定义见Context。 <br>Stage模型的应用Context定义见Context。 |
| name | string | 是 | 数据库名称，不能为空字符串且不能包含路径分隔符/。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

