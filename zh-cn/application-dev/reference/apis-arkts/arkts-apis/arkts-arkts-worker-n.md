# worker（线程管理）

```TypeScript
declare namespace worker
```

JS跨线程通信工具。Worker基于Actor并发模型，各线程运行环境相互隔离，通过序列化、引用传递或转移所有权传递对象。每个Actor具有消息队列和单线程执行模块，串行处理请求、发送请求并创建Actor。Actor异步交互，相互隔离且没有数据竞争。序列化支持除Symbol之外的基础类型、Date、String、RegExp、Array、Map、Set、Object、ArrayBuffer、TypedArray。普通Object仅传递属性，不传递原型及方法；通过自定义class创建的对象可以传递，但其函数属性及方法无法序列化传递。

**起始版本：** 7

<!--Device-unnamed-declare namespace worker--><!--Device-unnamed-declare namespace worker-End-->

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
| [workerPort](arkts-arkts-worker-con.md#workerport) | Worker线程用于与宿主线程通信的对象。 |
| [parentPort](arkts-arkts-worker-con.md#parentport) | Worker线程用于与宿主线程通信的对象。 |
