# RestrictedWorker（系统接口）

RestrictedWorker类包含所有Worker功能。

**继承/实现关系：** RestrictedWorker extends [ThreadWorker](arkts-arkts-worker-threadworker-c.md)

**起始版本：** 11

<!--Device-worker-class RestrictedWorker extends ThreadWorker--><!--Device-worker-class RestrictedWorker extends ThreadWorker-End-->

**系统能力：** SystemCapability.Utils.Lang

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { MessageEvents, PostMessageOptions, MessageEvent, Priority, WorkerEventTarget, ThreadWorkerPriority, ThreadWorkerGlobalScope, DedicatedWorkerGlobalScope, ErrorEvent, Event, EventListener, WorkerOptions, EventTarget, WorkerEventListener } from '@kit.ArkTS';
```

<a id="constructor"></a>
## constructor

```TypeScript
constructor(scriptURL: string, options?: WorkerOptions)
```

创建一个worker实例。

**起始版本：** 11

<!--Device-RestrictedWorker-constructor(scriptURL: string, options?: WorkerOptions)--><!--Device-RestrictedWorker-constructor(scriptURL: string, options?: WorkerOptions)-End-->

**系统能力：** SystemCapability.Utils.Lang

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scriptURL | string | 是 | scriptURL Worker线程执行的脚本URL。 |
| options | [WorkerOptions](arkts-arkts-worker-workeroptions-i.md) | 否 | 可为worker设置的选项。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200003](../errorcode-utils.md#10200003-worker初始化失败) | Worker initialization failure. |
| [10200007](../errorcode-utils.md#10200007-worker文件路径异常) | The worker file patch is invalid path. |

