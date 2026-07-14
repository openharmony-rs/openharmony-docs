# SequenceRunner

表示串行队列的任务，用于执行一组需要串行执行的任务。

**起始版本：** 11

**系统能力：** SystemCapability.Utils.Lang

## constructor

```TypeScript
constructor(priority?: Priority)
```

SequenceRunner的构造函数，用于创建一个**SequenceRunner**实例。

**起始版本：** 11

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| priority | Priority | 否 | 指定任务的优先级，默认值为**taskpool.Priority.MEDIUM**。 |

**示例：**

```TypeScript
let runner: taskpool.SequenceRunner = new taskpool.SequenceRunner();

```

## constructor

```TypeScript
constructor(name: string, priority?: Priority)
```

SequenceRunner的构造函数，用于创建一个**SequenceRunner**实例。该实例表示一个全局串行队列。如果传入的名字与已有名字相同，
将返回同一个串行队列。

> **说明**
>
> - 底层通过单例模式保证了：创建同名串行队列时，获取到同一个实例。
>
> - 无法修改串行队列的优先级。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 串行队列的名字。 |
| priority | Priority | 否 | 指定任务的优先级，默认值为**taskpool.Priority.MEDIUM**。 |

**示例：**

```TypeScript
let runner:taskpool.SequenceRunner = new taskpool.SequenceRunner("runner1", taskpool.Priority.LOW);

```

## execute

```TypeScript
execute(task: Task): Promise<Object>
```

执行串行任务。使用该方法前需先构造**SequenceRunner**实例。串行队列不能执行任务组任务、其他串行队列任务、异步队列任务、
有依赖关系的任务和已执行的任务。使用Promise异步回调。

> **说明**
>
> - 不支持加入存在依赖的任务。
>
> - 前面的任务执行失败或取消不会影响后续任务的执行。

**起始版本：** 11

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| task | Task | 是 | 需要添加到串行任务队列中的任务。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Object&gt; | Promise对象，返回任务执行的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200003](../errorcode-utils.md#10200003-worker初始化失败) | Worker initialization failed.<br>**适用版本：** 11 - 17 |
| [10200006](../errorcode-utils.md#10200006-worker传输信息序列化异常) | An exception occurred during serialization. |
| [10200025](../errorcode-utils.md#10200025-串行队列中添加了存在依赖的任务) | dependent task not allowed. |
| [10200051](../errorcode-utils.md#10200051-无法再次执行周期任务) | The periodic task cannot be executed again.<br>**适用版本：** 12+ |
| [10200057](../errorcode-utils.md#10200057-任务无法被两种api执行) | The task cannot be executed by two APIs.<br>**适用版本：** 18+ |

**示例：**

```TypeScript
@Concurrent
function additionDelay(delay: number): void {
  let start: number = new Date().getTime();
  while (new Date().getTime() - start < delay) {
    continue;
  }
}
@Concurrent
function waitForRunner(finalString: string): string {
  return finalString;
}
async function seqRunner() {
  let finalString:string = "";
  let task1:taskpool.Task = new taskpool.Task(additionDelay, 3000);
  let task2:taskpool.Task = new taskpool.Task(additionDelay, 2000);
  let task3:taskpool.Task = new taskpool.Task(additionDelay, 1000);
  let task4:taskpool.Task = new taskpool.Task(waitForRunner, finalString);

  let runner:taskpool.SequenceRunner = new taskpool.SequenceRunner();
  runner.execute(task1).then(() => {
    finalString += 'a';
    console.info("seqrunner: task1 done.");
  });
  runner.execute(task2).then(() => {
    finalString += 'b';
    console.info("seqrunner: task2 done");
  });
  runner.execute(task3).then(() => {
    finalString += 'c';
    console.info("seqrunner: task3 done");
  });
  await runner.execute(task4);
  console.info("seqrunner: task4 done, finalString is " + finalString);
}

```

