# attachGroup

## 导入模块

```TypeScript
import { request } from '@kit.BasicServicesKit';
import { cacheDownload } from '@kit.BasicServicesKit';
```

## attachGroup

```TypeScript
function attachGroup(gid: string, tids: string[]): Promise<void>
```

向指定分组id中绑定多个下载任务id。使用Promise异步回调。 如果任意一个任务id不满足添加条件，则所有列表中的任务都不会添加到分组中。

**起始版本：** 23

<!--Device-agent-function attachGroup(gid: string, tids: string[]): Promise<void>--><!--Device-agent-function attachGroup(gid: string, tids: string[]): Promise<void>-End-->

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
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br> 1. Missing mandatory parameters. <br> 2. Incorrect parameter type. <br> 3. Parameter verification failed. |
| [21900008](../errorcode-request.md#21900008-任务分组不存在或已移除) | Group deleted or not found. |
| [21900006](../errorcode-request.md#21900006-操作不存在的任务错误) | Task removed or not found. |
| [21900007](../errorcode-request.md#21900007-在不支持的状态上的操作) | Operation with wrong task state. |
| [21900005](../errorcode-request.md#21900005-任务模式错误) | Operation with wrong task mode. |
| [13400003](../errorcode-request.md#13400003-服务异常) | Task service ability error. |

**示例**

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 准备分组id和任务id列表。
let groupId: string = "123456789";
let taskIds: string[] = ["1111", "2222", "3333", "4444"];
// 调用 attachGroup 接口向分组中添加任务id列表。
request.agent.attachGroup(groupId, taskIds).then(() => {
  console.info(`Succeeded in attaching tasks to the download task group.`);
}).catch((err: Error) => {
  console.error(`Failed to attach tasks to the download group, Code: ${err.code}, message: ${err.message}`);
});
```

