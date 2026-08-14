# deleteGroup

## deleteGroup

```TypeScript
function deleteGroup(gid: string): Promise<void>
```

移除指定分组，后续不能再往该分组中添加任务id。使用Promise异步回调。 当分组中的所有任务处于完成、失败或移除状态，并且分组被移除时，显示该分组的完成或失败通知。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-agent-function deleteGroup(gid: string): Promise<void>--><!--Device-agent-function deleteGroup(gid: string): Promise<void>-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| gid | string | 是 | 目标分组id。与创建的任务分组ID保持一致，即使用 [request.agent.createGroup](arkts-basicservices-agent-creategroup-f.md#createGroup) 接口成功创建任务分组时的返回值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt; 1. Missing mandatory parameters. &lt;br&gt; 2. Incorrect parameter type. &lt;br&gt; 3. Parameter verification failed. |
| [21900008](../../apis-basic-services-kit/errorcode-request.md#21900008-任务分组不存在或已移除) | Group deleted or not found. |
| [13400003](../../apis-basic-services-kit/errorcode-request.md#13400003-服务异常) | Task service ability error. |

## 示例

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 准备分组id。
let groupId: string = "123456789";

// 调用 deleteGroup 接口移除分组。
request.agent.deleteGroup(groupId).then(() => {
  console.info(`Succeeded in deleting the download task group.`);
}).catch((err: Error) => {
  console.error(`Failed to delete the download group, Code: ${err.code}, message: ${err.message}`);
});
```

