# remove

## remove

```TypeScript
function remove(id: string, callback: AsyncCallback<void>): void
```

移除属于调用方的指定任务，如果正在处理中，该任务将被迫停止。使用callback异步回调。在调用后任务对象和其回调函数会被释放。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-agent-function remove(id: string, callback: AsyncCallback<void>): void--><!--Device-agent-function remove(id: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 任务id。 |
| callback | [AsyncCallback](arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当移除指定任务成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt; 1. Missing mandatory parameters. &lt;br&gt; 2. Incorrect parameter type. |
| [21900006](../../apis-basic-services-kit/errorcode-request.md#21900006-操作不存在的任务错误) | Task removed or not found. |
| [13400003](../../apis-basic-services-kit/errorcode-request.md#13400003-服务异常) | Task service ability error. |

## 示例

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

request.agent.remove("123456", (err: BusinessError<void> | null) => {
  if (err) {
    console.error(`Failed to remove a download task, Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in removing a download task.`);
});
```


## remove

```TypeScript
function remove(id: string): Promise<void>
```

移除属于调用方的指定任务，如果正在处理中，该任务将被迫停止。使用Promise异步回调。在调用后任务对象和其回调函数会被释放。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-agent-function remove(id: string): Promise<void>--><!--Device-agent-function remove(id: string): Promise<void>-End-->

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
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: &lt;br&gt; 1. Missing mandatory parameters. &lt;br&gt; 2. Incorrect parameter type. |
| [21900006](../../apis-basic-services-kit/errorcode-request.md#21900006-操作不存在的任务错误) | Task removed or not found. |
| [13400003](../../apis-basic-services-kit/errorcode-request.md#13400003-服务异常) | Task service ability error. |

## 示例

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

request.agent.remove("123456").then(() => {
  console.info(`Succeeded in removing a download task. `);
}).catch((err: Error) => {
  console.error(`Failed to remove a download task, Code: ${err.code}, message: ${err.message}`);
});
```

