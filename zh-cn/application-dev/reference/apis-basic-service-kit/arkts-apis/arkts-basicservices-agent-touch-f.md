# touch

## touch

```TypeScript
function touch(id: string, token: string, callback: AsyncCallback<TaskInfo>): void
```

根据任务id和token查询任务的详细信息。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-agent-function touch(id: string, token: string, callback: AsyncCallback<TaskInfo>): void--><!--Device-agent-function touch(id: string, token: string, callback: AsyncCallback<TaskInfo>): void-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 任务id。 |
| token | string | 是 | 任务查询token。 |
| callback | [AsyncCallback](arkts-basicservices-asynccallback-t.md)&lt;TaskInfo&gt; | 是 | 回调函数。当查询任务操作成功，err为undefined，data为查询到的任务TaskInfo信息；否则为错误对象。 |

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

request.agent.touch("123456", "token", (err: BusinessError<void> | null, taskInfo: request.agent.TaskInfo | undefined) => {
  if (err) {
    console.error(`Failed to touch a upload task, Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in touching a upload task.`);
});
```


## touch

```TypeScript
function touch(id: string, token: string): Promise<TaskInfo>
```

根据任务id和token查询任务的详细信息。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-agent-function touch(id: string, token: string): Promise<TaskInfo>--><!--Device-agent-function touch(id: string, token: string): Promise<TaskInfo>-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 任务id。 |
| token | string | 是 | 任务查询token。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;TaskInfo&gt; | Promise对象。返回任务详细信息TaskInfo的Promise对象。 |

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

request.agent.touch("123456", "token").then((taskInfo: request.agent.TaskInfo) => {
  console.info(`Succeeded in touching a upload task. `);
}).catch((err: Error) => {
  console.error(`Failed to touch a upload task, Code: ${err.code}, message: ${err.message}`);
});
```

