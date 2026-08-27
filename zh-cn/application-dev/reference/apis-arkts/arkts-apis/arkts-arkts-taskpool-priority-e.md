# Priority

表示所创建任务（Task）执行时的优先级。工作线程优先级跟随任务优先级更新，对应关系参考QoS等级定义。

**起始版本：** 9

**系统能力：** SystemCapability.Utils.Lang

## HIGH

```TypeScript
HIGH = 0
```

任务为高优先级。从API version 11开始，该接口支持在原子化服务中使用。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## MEDIUM

```TypeScript
MEDIUM = 1
```

任务为中优先级。从API version 11开始，该接口支持在原子化服务中使用。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## LOW

```TypeScript
LOW = 2
```

任务为低优先级。从API version 11开始，该接口支持在原子化服务中使用。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## IDLE

```TypeScript
IDLE = 3
```

任务为后台任务。从API version 12开始，该接口支持在原子化服务中使用。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**示例**

```TypeScript
@Concurrent
function printArgs(args: number): number {
  let t: number = Date.now();
  while (Date.now() - t < 1000) { // 1000: delay 1s
    continue;
  }
  console.info("printArgs: " + args);
  return args;
}

let allCount = 100; // 100: test number
let taskArray: Array<taskpool.Task> = [];
// 创建400个任务并添加至taskArray
for (let i: number = 0; i < allCount; i++) {
  let task1: taskpool.Task = new taskpool.Task(printArgs, i);
  taskArray.push(task1);
  let task2: taskpool.Task = new taskpool.Task(printArgs, i * 10); // 10: test number
  taskArray.push(task2);
  let task3: taskpool.Task = new taskpool.Task(printArgs, i * 100); // 100: test number
  taskArray.push(task3);
  let task4: taskpool.Task = new taskpool.Task(printArgs, i * 1000); // 1000: test number
  taskArray.push(task4);
}

// 从taskArray中获取不同的任务并给定不同优先级执行
for (let i: number = 0; i < taskArray.length; i+=4) { // 4: 每次执行4个任务，循环取任务时需后移4项，确保执行的是不同的任务
  taskpool.execute(taskArray[i], taskpool.Priority.HIGH);
  taskpool.execute(taskArray[i + 1], taskpool.Priority.LOW);
  taskpool.execute(taskArray[i + 2], taskpool.Priority.MEDIUM);
  taskpool.execute(taskArray[i + 3], taskpool.Priority.IDLE);
}
```
