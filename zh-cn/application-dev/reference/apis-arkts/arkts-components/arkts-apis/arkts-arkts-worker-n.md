# worker(线程管理)

JS跨线程通信工具。

**起始版本：** 7

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { worker, DedicatedWorkerGlobalScope, ErrorEvent, Event, EventListener, EventTarget, MessageEvent, MessageEvents, PostMessageOptions, ThreadWorkerGlobalScope, WorkerEventListener, WorkerEventTarget, WorkerOptions, ThreadWorkerPriority, Priority } from '@kit.ArkTS';
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
| [RestrictedWorker](arkts-arkts-worker-restrictedworker-c-sys.md) | RestrictedWorker类继承[ThreadWorker](arkts-arkts-worker-threadworker-c.md)，具有ThreadWorker中所有的方法。RestrictedWorker主要用于提供受限的Worker线程运行环境，该线程运行环境中只允许导入Worker模块，不允许导入其他API。 |
<!--DelEnd-->

### 常量

| 名称 | 说明 |
| --- | --- |
| [parentPort](arkts-arkts-worker-con.md#parentport) | Worker线程用于与宿主线程通信的对象。 |
| [workerPort](arkts-arkts-worker-con.md#workerport) | Worker线程用于与宿主线程通信的对象。 |
