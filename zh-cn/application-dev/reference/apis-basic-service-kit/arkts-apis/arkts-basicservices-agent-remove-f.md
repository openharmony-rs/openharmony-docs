# remove

## remove

```TypeScript
function remove(id: string, callback: AsyncCallback<void>): void
```

移除属于调用方的指定任务，如果正在处理中，该任务将被迫停止。使用callback异步回调。在调用后任务对象和其回调函数会被释放。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 任务id。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当移除指定任务成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Missing mandatory parameters.<br/><br/>2. Incorrect parameter type. |
| [13400003](../../errorcode-universal.md#13400003-Task) | Task service ability error. |
| [21900006](../../errorcode-universal.md#21900006-Task) | Task removed or not found. |


## remove

```TypeScript
function remove(id: string): Promise<void>
```

移除属于调用方的指定任务，如果正在处理中，该任务将被迫停止。使用Promise异步回调。在调用后任务对象和其回调函数会被释放。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 任务id。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Missing mandatory parameters.<br/><br/>2. Incorrect parameter type. |
| [13400003](../../errorcode-universal.md#13400003-Task) | Task service ability error. |
| [21900006](../../errorcode-universal.md#21900006-Task) | Task removed or not found. |

