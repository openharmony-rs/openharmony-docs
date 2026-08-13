# getTask

## getTask

```TypeScript
function getTask(context: BaseContext, id: string, token?: string): Promise<Task>
```

根据任务id查询任务。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-agent-function getTask(context: BaseContext, id: string, token?: string): Promise<Task>--><!--Device-agent-function getTask(context: BaseContext, id: string, token?: string): Promise<Task>-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [BaseContext](../../apis-ability-kit/arkts-apis/arkts-ability-basecontext-c.md) | 是 | 基于应用程序的上下文。 |
| id | string | 是 | 任务id。 |
| token | string | 否 | 任务查询token。默认值为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Task&gt; | Promise对象。返回任务配置信息的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt; 1. Missing mandatory parameters. &lt;br&gt; 2. Incorrect parameter type. &lt;br&gt; 3. Parameter verification failed. |
| [21900006](../../apis-basic-services-kit/errorcode-request.md#21900006-操作不存在的任务错误) | Task removed or not found. |
| [13400003](../../apis-basic-services-kit/errorcode-request.md#13400003-服务异常) | Task service ability error. |

## 示例

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
request.agent.getTask(context, "123456").then((task: request.agent.Task) => {
  console.info(`Succeeded in querying a task. result: ${task.tid}`);
}).catch((err: Error) => {
  console.error(`Failed to query a task, Code: ${err.code}, message: ${err.message}`);
});
```

