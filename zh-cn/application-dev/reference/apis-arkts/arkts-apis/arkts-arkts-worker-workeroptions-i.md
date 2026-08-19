# WorkerOptions

Worker构造函数的选项，用于为Worker添加其他信息。

**起始版本：** 7

<!--Device-unnamed-export interface WorkerOptions--><!--Device-unnamed-export interface WorkerOptions-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { worker, DedicatedWorkerGlobalScope, ErrorEvent, Event, EventListener, EventTarget, MessageEvent, MessageEvents, PostMessageOptions, ThreadWorkerGlobalScope, WorkerEventListener, WorkerEventTarget, WorkerOptions, ThreadWorkerPriority, Priority } from '@kit.ArkTS';
```

## name

```TypeScript
name?: string
```

Worker的名称。默认值为undefined，此时线程名称为'WorkerThread'。 非默认值情况下，对应的线程名称带有'WorkerThread_'前缀。比如name为'testName'时，对应的线程名称为'WorkerThread_testName'。 线程名称可通过HeapMemoryInfo的threadName获取。

**类型：** string

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WorkerOptions-name?: string--><!--Device-WorkerOptions-name?: string-End-->

**系统能力：** SystemCapability.Utils.Lang

## priority

```TypeScript
priority?: ThreadWorkerPriority
```

表示Worker线程优先级。默认值为MEDIUM。

**类型：** [ThreadWorkerPriority](arkts-arkts-worker-threadworkerpriority-e.md)

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-WorkerOptions-priority?: ThreadWorkerPriority--><!--Device-WorkerOptions-priority?: ThreadWorkerPriority-End-->

**系统能力：** SystemCapability.Utils.Lang

## shared

```TypeScript
shared?: boolean
```

表示Worker共享功能，此接口暂不支持。

**类型：** boolean

**起始版本：** 7

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WorkerOptions-shared?: boolean--><!--Device-WorkerOptions-shared?: boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

## type

```TypeScript
type?: 'classic' | 'module'
```

Worker执行脚本的模式类型，暂不支持module类型，默认值为classic。

**类型：** 'classic' \| 'module'

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WorkerOptions-type?: 'classic' | 'module'--><!--Device-WorkerOptions-type?: 'classic' | 'module'-End-->

**系统能力：** SystemCapability.Utils.Lang

