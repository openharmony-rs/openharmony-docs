# @ohos.worker(线程管理)

JS跨线程通信工具。Worker基于Actor并发模型，各线程运行环境相互隔离，通过序列化、引用传递或转移所有权传递对象。每个Actor具有消息队列和单线程执行模块，串行处理请求、发送请求并创建Actor。Actor异步交互，相互隔离且没有数据竞争。序列化支持除Symbol之外的基础类型、Date、String、RegExp、Array、Map、Set、Object、ArrayBuffer、TypedArray。普通Object仅传递属性，不传递原型及方法；通过自定义class创建的对象可以传递，但其函数属性及方法无法序列化传递。

## 导入模块

```TypeScript
import { worker, DedicatedWorkerGlobalScope, ErrorEvent, Event, EventListener, EventTarget, MessageEvent, MessageEvents, PostMessageOptions, ThreadWorkerGlobalScope, WorkerEventListener, WorkerEventTarget, WorkerOptions, ThreadWorkerPriority, Priority } from '@kit.ArkTS';
```

## 汇总

### 命名空间

| 名称 | 说明 |
| --- | --- |
| [worker](arkts-arkts-worker-n.md) | JS跨线程通信工具。Worker基于Actor并发模型，各线程运行环境相互隔离，通过序列化、引用传递或转移所有权传递对象。每个Actor具有消息队列和单线程执行模块，串行处理请求、发送请求并创建Actor。Actor异步交互，相互隔离且没有数据竞争。序列化支持除Symbol之外的基础类型、Date、String、RegExp、Array、Map、Set、Object、ArrayBuffer、TypedArray。普通Object仅传递属性，不传递原型及方法；通过自定义class创建的对象可以传递，但其函数属性及方法无法序列化传递。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ErrorEvent](arkts-arkts-worker-errorevent-i.md) | 错误事件类用于表示Worker执行过程中出现异常的详细信息，ErrorEvent类继承Event。 |
| [Event](arkts-arkts-worker-event-i.md) | 事件类。 |
| [GlobalScope](arkts-arkts-worker-globalscope-i.md) | Worker线程自身的运行环境，GlobalScope类继承WorkerEventTarget。 |
| [MessageEvent](arkts-arkts-worker-messageevent-i.md) | 消息类，持有Worker线程间传递的数据，MessageEvent类继承Event。 |
| [MessageEvents](arkts-arkts-worker-messageevents-i.md) | 消息类，持有Worker线程间传递的数据。 |
| [PostMessageOptions](arkts-arkts-worker-postmessageoptions-i.md) | 明确数据传递过程中需要转移所有权的对象，这些对象必须是ArrayBuffer，在发送方的上下文中将变为不可用，仅在接收方可用。 |
| [ThreadWorkerGlobalScope](arkts-arkts-worker-threadworkerglobalscope-i.md) | Worker线程用于与宿主线程通信的类。其中postMessage接口用于向宿主线程发送消息，close接口用于销毁Worker线程。ThreadWorkerGlobalScope类继承GlobalScope9+。 |
| [WorkerEventListener](arkts-arkts-worker-workereventlistener-i.md) | 事件监听类。 |
| [WorkerEventTarget](arkts-arkts-worker-workereventtarget-i.md) | 用于管理Worker的监听事件。 |
| [WorkerOptions](arkts-arkts-worker-workeroptions-i.md) | Worker构造函数的选项，用于为Worker添加其他信息。 |
| [DedicatedWorkerGlobalScope](arkts-arkts-worker-dedicatedworkerglobalscope-i.md) | Worker线程自身的运行环境，与宿主线程环境隔离。 |
| [EventListener](arkts-arkts-worker-eventlistener-i.md) | 事件监听类用于处理事件。 |
| [EventTarget](arkts-arkts-worker-eventtarget-i.md) | 用于管理Worker的监听事件。 |
| [WorkerGlobalScope](arkts-arkts-worker-workerglobalscope-i.md) | Worker线程自身的运行环境，与宿主线程环境隔离。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ErrorCallback](arkts-arkts-errorcallback-t.md) | 表示异常回调类型。 |
| [MessageType](arkts-arkts-messagetype-t.md) | 表示消息类型。预留数据类型，暂未实现。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [Priority](arkts-arkts-worker-priority-e.md) | 表示发送消息时的优先级枚举，各优先级对应关系请参考EventHandler等级定义。 |
| [ThreadWorkerPriority](arkts-arkts-worker-threadworkerpriority-e.md) | Worker线程的优先级枚举，各优先级对应关系请参考QoS等级定义。 |
