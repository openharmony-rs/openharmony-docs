# @ohos.worker

JS跨线程通信工具。

## 汇总

### 命名空间

| 名称 | 说明 |
| --- | --- |
| [worker](arkts-arkts-worker-n.md) | JS跨线程通信工具。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [DedicatedWorkerGlobalScope](arkts-arkts-dedicatedworkerglobalscope-i.md) | Worker线程自身的运行环境，与宿主线程环境隔离。 |
| [ErrorEvent](arkts-arkts-errorevent-i.md) | 错误事件类用于表示Worker执行过程中出现异常的详细信息，ErrorEvent类继承Event。 |
| [Event](arkts-arkts-event-i.md) | 事件类。 |
| [EventListener](arkts-arkts-eventlistener-i.md) | 事件监听类用于处理事件。 |
| [EventTarget](arkts-arkts-eventtarget-i.md) | 用于管理Worker的监听事件。 |
| [GlobalScope](arkts-arkts-globalscope-i.md) | Worker线程自身的运行环境，GlobalScope类继承WorkerEventTarget。 |
| [MessageEvent](arkts-arkts-messageevent-i.md) | 消息类，持有Worker线程间传递的数据，MessageEvent类继承Event。 |
| [MessageEvents](arkts-arkts-messageevents-i.md) | 消息类，持有Worker线程间传递的数据。 |
| [PostMessageOptions](arkts-arkts-postmessageoptions-i.md) | 明确数据传递过程中需要转移所有权的对象，这些对象必须是ArrayBuffer，在发送方的上下文中将变为不可用，仅在接收方可用。 |
| [ThreadWorkerGlobalScope](arkts-arkts-threadworkerglobalscope-i.md) | Worker线程用于与宿主线程通信的类。其中postMessage接口用于向宿主线程发送消息，close接口用于销毁Worker线程。ThreadWorkerGlobalScope类继承GlobalScope9+。 |
| [WorkerEventListener](arkts-arkts-workereventlistener-i.md) | 事件监听类。 |
| [WorkerEventTarget](arkts-arkts-workereventtarget-i.md) | 用于管理Worker的监听事件。 |
| [WorkerGlobalScope](arkts-arkts-workerglobalscope-i.md) | Worker线程自身的运行环境，与宿主线程环境隔离。 |
| [WorkerOptions](arkts-arkts-workeroptions-i.md) | Worker构造函数的选项，用于为Worker添加其他信息。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [Priority](arkts-arkts-priority-e.md) | 表示发送消息时的优先级枚举，各优先级对应关系请参考EventHandler等级定义。 |
| [ThreadWorkerPriority](arkts-arkts-threadworkerpriority-e.md) | Worker线程的优先级枚举，各优先级对应关系请参考QoS等级定义。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ErrorCallback](arkts-arkts-errorcallback-t.md) | 表示异常回调类型。 |
| [MessageType](arkts-arkts-messagetype-t.md) | 表示消息类型。预留数据类型，暂未实现。 |

