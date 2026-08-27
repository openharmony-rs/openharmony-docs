# RestrictedWorker（系统接口）

RestrictedWorker类继承[ThreadWorker](arkts-arkts-worker-threadworker-c.md)，具有ThreadWorker中所有的方法。 RestrictedWorker主要用于提供受限的Worker线程运行环境，该线程运行环境中只允许导入Worker模块，不允许导入其他API。

**继承/实现关系：** RestrictedWorker extends [ThreadWorker](arkts-arkts-worker-threadworker-c.md)

**起始版本：** 11

**系统能力：** SystemCapability.Utils.Lang

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { worker, DedicatedWorkerGlobalScope, ErrorEvent, Event, EventListener, EventTarget, MessageEvent, MessageEvents, PostMessageOptions, ThreadWorkerGlobalScope, WorkerEventListener, WorkerEventTarget, WorkerOptions, ThreadWorkerPriority, Priority } from '@kit.ArkTS';
```

## constructor

```TypeScript
constructor(scriptURL: string, options?: WorkerOptions)
```

RestrictedWorker构造函数。使用其他方法前，均需先构造RestrictedWorker实例。

**起始版本：** 11

**系统能力：** SystemCapability.Utils.Lang

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scriptURL | string | 是 | Worker线程文件的路径，路径规则详细参考文件路径注意事项。 |
| options | [WorkerOptions](arkts-arkts-worker-workeroptions-i.md) | 否 | 构造RestrictedWorker时的选项。type默认值为'classic'，name默认'undefined'， shared默认'undefined'，priority默认'MEDIUM'。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200003](../errorcode-utils.md#10200003-worker初始化失败) | Worker initialization failure. |
| [10200007](../errorcode-utils.md#10200007-worker文件路径异常) | The worker file path is invalid. |

**示例**

以下示例展示了在Stage模型的entry模块Index.ets文件中加载Worker线程文件的方法，使用Library加载Worker线程文件的场景参考[文件路径注意事项](../../../arkts-utils/worker-introduction.md#文件路径注意事项)。

```TypeScript
// Index.ets
import { worker } from '@kit.ArkTS';

// worker文件所在路径："entry/src/main/ets/workers/worker.ets"
const workerInstance = new worker.ThreadWorker('entry/ets/workers/worker.ets', {name: "WorkerThread"});
```

此处以在Stage模型的entry模块Index.ets文件中加载Worker线程文件为例，使用Library加载Worker线程文件的场景参考[文件路径注意事项](../../../arkts-utils/worker-introduction.md#文件路径注意事项)。

```TypeScript
// Index.ets
import { worker } from '@kit.ArkTS';

// worker文件所在路径："entry/src/main/ets/workers/worker.ets"
const workerInstance = new worker.Worker('entry/ets/workers/worker.ets', {name: "WorkerThread"});
```
