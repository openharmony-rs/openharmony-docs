# GenericsTask

表示泛型任务。**GenericsTask**继承自
[Task](arkts-arkts-execute-f.md#execute-1)。
相比创建Task，创建GenericsTask可以在编译阶段校验并发函数的传参和返回值类型。其余行为与Task相同。

**继承/实现关系：** GenericsTask extends [Task](arkts-arkts-task-c.md)

**起始版本：** 13

**系统能力：** SystemCapability.Utils.Lang

## constructor

```TypeScript
constructor(func: (...args: A) => R | Promise<R>, ...args: A)
```

GenericsTask的构造函数，用于创建一个**GenericsTask**对象。

**起始版本：** 13

**元服务API：** 从API版本13开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| func | (...args: A) =&gt; R \| Promise&lt;R&gt; | 是 | 执行的逻辑需要传入函数，该函数必须使用[@Concurrent装饰器](../../../../arkts-utils/taskpool-introduction.md#concurrent装饰器)装饰。支持的函数返回值类型请参考[序列化支持类型](../../../../reference/apis-arkts/js-apis-taskpool.md#序列化支持类型)。 |
| args | A | 是 | 任务执行传入函数的入参，支持的参数类型请参考[序列化支持类型](../../../../reference/apis-arkts/js-apis-taskpool.md#序列化支持类型)。默认值为**undefined**。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200014](../errorcode-utils.md#10200014-非concurrent函数错误) | The function is not marked as concurrent. |

**示例：**

```TypeScript
@Concurrent
function printArgs(args: string): string {
  console.info("printArgs: " + args);
  return args;
}

@Concurrent
function testWithThreeParams(a: number, b: string, c: number): string {
  return b;
}

@Concurrent
function testWithArray(args: [number, string]): string {
  return "success";
}

let task1: taskpool.Task = new taskpool.GenericsTask<[string], string>(printArgs, "this is my first LongTask");

let task2: taskpool.Task = new taskpool.GenericsTask<[number, string, number], string>(testWithThreeParams, 100, "test", 100);

let task3: taskpool.Task = new taskpool.GenericsTask<[[number, string]], string>(testWithArray, [100, "test"]);

```

## constructor

```TypeScript
constructor(name: string, func: (...args: A) => R | Promise<R>, ...args: A)
```

GenericsTask的构造函数，用于创建一个**GenericsTask**实例，并可指定任务名称。

**起始版本：** 13

**元服务API：** 从API版本13开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 泛型任务名称。 |
| func | (...args: A) =&gt; R \| Promise&lt;R&gt; | 是 | 执行的逻辑需要传入函数，该函数必须使用[@Concurrent装饰器](../../../../arkts-utils/taskpool-introduction.md#concurrent装饰器)装饰。支持的函数返回值类型请参考[序列化支持类型](../../../../reference/apis-arkts/js-apis-taskpool.md#序列化支持类型)。 |
| args | A | 是 | 任务执行传入函数的入参，支持的参数类型请参考[序列化支持类型](../../../../reference/apis-arkts/js-apis-taskpool.md#序列化支持类型)。默认值为**undefined**。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200014](../errorcode-utils.md#10200014-非concurrent函数错误) | The function is not marked as concurrent. |

**示例：**

```TypeScript
@Concurrent
function printArgs(args: string): string {
  console.info("printArgs: " + args);
  return args;
}

let taskName: string = "taskName";
let task: taskpool.Task = new taskpool.GenericsTask<[string], string>(taskName, printArgs, "this is my first Task");
let name: string = task.name;

```

