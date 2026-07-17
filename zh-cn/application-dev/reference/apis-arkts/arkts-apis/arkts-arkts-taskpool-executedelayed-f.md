# executeDelayed

## 导入模块

```TypeScript
import { taskpool } from '@kit.ArkTS';
```

## executeDelayed

```TypeScript
function executeDelayed(delayTime: number, task: Task, priority?: Priority): Promise<Object>
```

延时执行任务。当前执行模式可以设置任务优先级，并且可以尝试调用**cancel()**取消执行。该任务不能是任务组任务、串行队列任务、异步队列任务或周期任务。对于长时任务，仅支持执行一次；对于非长时任务，可以多次调用。使用Promise异步回调。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-taskpool-function executeDelayed(delayTime: number, task: Task, priority?: Priority): Promise<Object>--><!--Device-taskpool-function executeDelayed(delayTime: number, task: Task, priority?: Priority): Promise<Object>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| delayTime | number | 是 | 延时时间，单位为ms。delayTime值必须要大于等于0。该值应为整数。<br>单位：毫秒。 |
| task | [Task](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-agent-task-i.md) | 是 | 需要延时执行的任务。 |
| priority | [Priority](arkts-arkts-taskpool-priority-e.md) | 否 | 延时执行的任务的优先级，默认值为**taskpool.Priority.MEDIUM**。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Object> | Promise对象，返回任务函数的执行结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200028](../errorcode-utils.md#10200028-延时时间小于零) | The delayTime is less than zero. |
| [10200006](../errorcode-utils.md#10200006-worker传输信息序列化异常) | An exception occurred during serialization.<br>**适用版本：** 12+ |
| [10200014](../errorcode-utils.md#10200014-非concurrent函数错误) | The function is not marked as concurrent.<br>**适用版本：** 12+ |
| [10200051](../errorcode-utils.md#10200051-无法再次执行周期任务) | The periodic task cannot be executed again.<br>**适用版本：** 12+ |
| [10200057](../errorcode-utils.md#10200057-任务无法被两种api执行) | The task cannot be executed by two APIs.<br>**适用版本：** 18+ |

**示例：**

```TypeScript
// import BusinessError
import { BusinessError } from '@kit.BasicServicesKit';

@Concurrent
function printArgs(args: number): void {
    console.info("printArgs: " + args);
}

let t: number = Date.now();
console.info("taskpool start time is: " + t);
let task: taskpool.Task = new taskpool.Task(printArgs, 100); // 100: test number
taskpool.executeDelayed(1000, task).then(() => { // 1000: delayTime is 1000ms
  console.info('Succeeded in executing task');
}).catch((e: BusinessError) => {
  console.error(`Failed to execute task. Code: ${e.code}, message: ${e.message}`);
})

```


## executeDelayed

```TypeScript
function executeDelayed<A extends Array<Object>, R>(delayTime: number, task: GenericsTask<A, R>, priority?: Priority): Promise<R>
```

延时执行泛型任务，不校验任务的参数类型和返回值类型。使用Promise异步回调。executeDelayed任务的校验是结合**new GenericsTask**一起用的，参数、返回值类型需与**new GenericsTask**中的类型保持一致。

**起始版本：** 13

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-taskpool-function executeDelayed<A extends Array<Object>, R>(delayTime: number, task: GenericsTask<A, R>, priority?: Priority): Promise<R>--><!--Device-taskpool-function executeDelayed<A extends Array<Object>, R>(delayTime: number, task: GenericsTask<A, R>, priority?: Priority): Promise<R>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| delayTime | number | 是 | 延时时间，单位为ms。delayTime值必须要大于等于0。该值应为整数。<br>单位：毫秒。 |
| task | [GenericsTask](arkts-arkts-taskpool-genericstask-c.md)<A, R> | 是 | 需要延时执行的泛型任务。 |
| priority | [Priority](arkts-arkts-taskpool-priority-e.md) | 否 | 延时执行的任务的优先级，默认值为**taskpool.Priority.MEDIUM**。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<R> | Promise对象，返回任务函数的执行结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200028](../errorcode-utils.md#10200028-延时时间小于零) | The delayTime is less than zero. |
| [10200051](../errorcode-utils.md#10200051-无法再次执行周期任务) | The periodic task cannot be executed again. |
| [10200057](../errorcode-utils.md#10200057-任务无法被两种api执行) | The task cannot be executed by two APIs.<br>**适用版本：** 18+ |

**示例：**

```TypeScript
// import BusinessError
import { BusinessError } from '@kit.BasicServicesKit'

@Concurrent
function printArgs(args: number): string {
    console.info("printArgs: " + args);
    return "success";
}

let task: taskpool.Task = new taskpool.GenericsTask<[number], string>(printArgs, 100); // 100: test number
taskpool.executeDelayed<[number], string>(1000, task).then((res: string) => { // 1000: delayTime is 1000ms
  console.info('Succeeded in executing task');
}).catch((e: BusinessError) => {
  console.error(`Failed to execute task. Code: ${e.code}, message: ${e.message}`);
})

```

