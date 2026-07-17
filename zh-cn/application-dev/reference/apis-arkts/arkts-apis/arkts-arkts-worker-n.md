# worker

JS跨线程通信工具。

**起始版本：** 7

<!--Device-unnamed-declare namespace worker--><!--Device-unnamed-declare namespace worker-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { MessageEvents, PostMessageOptions, MessageEvent, Priority, WorkerEventTarget, ThreadWorkerPriority, ThreadWorkerGlobalScope, DedicatedWorkerGlobalScope, ErrorEvent, Event, EventListener, WorkerOptions, EventTarget, WorkerEventListener } from '@kit.ArkTS';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [ThreadWorker](arkts-arkts-worker-threadworker-c.md) | 使用以下方法前，需先构造ThreadWorker实例。ThreadWorker类继承WorkerEventTarget。 |
| [Worker](arkts-arkts-worker-worker-c.md) | Worker类包含所有Worker功能。 |

<!--Del-->
### 类（系统接口）

| 名称 | 说明 |
| --- | --- |
| [RestrictedWorker](arkts-arkts-worker-restrictedworker-c-sys.md) | RestrictedWorker类包含所有Worker功能。 |
<!--DelEnd-->

### 常量

| 名称 | 说明 |
| --- | --- |
| [parentPort](arkts-arkts-worker-con.md#parentport) | Worker线程用于与宿主线程通信的对象。 |
| [workerPort](arkts-arkts-worker-con.md#workerport) | Worker线程用于与宿主线程通信的对象。 |

