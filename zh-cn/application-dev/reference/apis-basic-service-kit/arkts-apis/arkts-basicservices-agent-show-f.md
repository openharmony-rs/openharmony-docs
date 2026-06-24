# show

## show

```TypeScript
function show(id: string, callback: AsyncCallback<TaskInfo>): void
```

根据任务id查询任务的详细信息。使用callback异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 任务id。 |
| callback | AsyncCallback&lt;TaskInfo&gt; | 是 | 回调函数。当查询任务操作成功，err为undefined，data为查询到的任务TaskInfo信息；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Missing mandatory parameters.<br/><br/>2. Incorrect parameter type. |
| [13400003](../../errorcode-universal.md#13400003-Task) | Task service ability error. |
| [21900006](../../errorcode-universal.md#21900006-Task) | Task removed or not found. |


## show

```TypeScript
function show(id: string): Promise<TaskInfo>
```

根据任务id查询任务的详细信息。使用Promise异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 任务id。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;TaskInfo&gt; | Promise对象。返回任务详细信息TaskInfo的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Missing mandatory parameters.<br/><br/>2. Incorrect parameter type. |
| [13400003](../../errorcode-universal.md#13400003-Task) | Task service ability error. |
| [21900006](../../errorcode-universal.md#21900006-Task) | Task removed or not found. |

