# getTask

## getTask

```TypeScript
function getTask(context: BaseContext, id: string, token?: string): Promise<Task>
```

根据任务id查询任务。使用Promise异步回调。

**起始版本：** 11

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | BaseContext | 是 | 基于应用程序的上下文。 |
| id | string | 是 | 任务id。 |
| token | string | 否 | 任务查询token。默认值为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Task&gt; | Promise对象。返回任务配置信息的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Missing mandatory parameters.<br> 2. Incorrect parameter type.<br> 3. Parameter verification failed. |
| [13400003](../../apis-basic-services-kit/errorcode-request.md#13400003-服务异常) | Task service ability error. |
| [21900006](../../apis-basic-services-kit/errorcode-request.md#21900006-操作不存在的任务错误) | Task removed or not found. |

