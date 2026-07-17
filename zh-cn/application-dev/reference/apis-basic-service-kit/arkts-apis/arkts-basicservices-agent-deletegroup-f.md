# deleteGroup

## 导入模块

```TypeScript
import { request } from '@kit.BasicServicesKit';
```

## deleteGroup

```TypeScript
function deleteGroup(gid: string): Promise<void>
```

移除指定分组，后续不能再往该分组中添加任务id。使用Promise异步回调。

当分组中的所有任务处于完成、失败或移除状态，并且分组被移除时，显示该分组的完成或失败通知。

**起始版本：** 15

<!--Device-agent-function deleteGroup(gid: string): Promise<void>--><!--Device-agent-function deleteGroup(gid: string): Promise<void>-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| gid | string | 是 | 目标分组id。与创建的任务分组ID保持一致，即使用[request.agent.createGroup](arkts-basicservices-agent-creategroup-f.md#creategroup-1)接口成功创建任务分组时的返回值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Missing mandatory parameters.<br> 2. Incorrect parameter type.<br> 3. Parameter verification failed. |
| [13400003](../../apis-basic-services-kit/errorcode-request.md#13400003-服务异常) | Task service ability error. |
| [21900008](../../apis-basic-services-kit/errorcode-request.md#21900008-任务分组不存在或已移除) | Group deleted or not found. |

