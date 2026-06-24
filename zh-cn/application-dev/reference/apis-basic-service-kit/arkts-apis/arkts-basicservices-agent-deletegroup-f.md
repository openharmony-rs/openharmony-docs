# deleteGroup

## deleteGroup

```TypeScript
function deleteGroup(gid: string): Promise<void>
```

移除指定分组，后续不能再往该分组中添加任务id。使用Promise异步回调。

当分组中的所有任务处于完成、失败或移除状态，并且分组被移除时，显示该分组的完成或失败通知。

**起始版本：** 15

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| gid | string | 是 | 目标分组id。与创建的任务分组ID保持一致，即使用<br/>[request.agent.createGroup](arkts-basicservices-agent-creategroup-f.md#createGroup-1)<br/>接口成功创建任务分组时的返回值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Missing mandatory parameters.<br/><br/>2. Incorrect parameter type.<br/><br/>3. Parameter verification failed. |
| [13400003](../../errorcode-universal.md#13400003-Task) | Task service ability error. |
| [21900008](../../errorcode-universal.md#21900008-Group) | Group deleted or not found. |

