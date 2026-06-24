# attachGroup

## attachGroup

```TypeScript
function attachGroup(gid: string, tids: string[]): Promise<void>
```

向指定分组id中绑定多个下载任务id。使用Promise异步回调。

如果任意一个任务id不满足添加条件，则所有列表中的任务都不会添加到分组中。

**起始版本：** 15

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| gid | string | 是 | 目标分组id。 |
| tids | string[] | 是 | 待绑定的任务id列表。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Missing mandatory parameters.<br/><br/>2. Incorrect parameter type.<br/><br/>3. Parameter verification failed. |
| [13400003](../../errorcode-universal.md#13400003-Task) | Task service ability error. |
| [21900005](../../errorcode-universal.md#21900005-Operation) | Operation with wrong task mode. |
| [21900006](../../errorcode-universal.md#21900006-Task) | Task removed or not found. |
| [21900007](../../errorcode-universal.md#21900007-Operation) | Operation with wrong task state. |
| [21900008](../../errorcode-universal.md#21900008-Group) | Group deleted or not found. |

