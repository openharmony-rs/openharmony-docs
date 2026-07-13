# WorkerEventListener

事件监听类。

**起始版本：** 9

**系统能力：** SystemCapability.Utils.Lang

## constructor

```TypeScript
(event: Event): void | Promise<void>
```

指定要调用的回调函数。

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | Event | 是 | 回调的事件类。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200004](../errorcode-utils.md#10200004-worker处于非运行状态) | The Worker instance is not running. |
| [10200005](../errorcode-utils.md#10200005-worker不支持某api) | The called API is not supported in the worker thread. |

**示例：**

```TypeScript
// Index.ets
import { worker, Event } from "@kit.ArkTS"

const workerInstance = new worker.ThreadWorker("entry/ets/workers/worker.ets");

workerInstance.addEventListener("alert", (event: Event) => {
  console.info("event type is: ", JSON.stringify(event.type));
});

const eventToDispatch : Event = { type: "alert", timeStamp: 0 }; // timeStamp暂未支持
workerInstance.dispatchEvent(eventToDispatch);

```

