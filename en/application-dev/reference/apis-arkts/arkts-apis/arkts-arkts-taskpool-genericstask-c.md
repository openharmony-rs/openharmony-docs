# GenericsTask

```TypeScript
class GenericsTask<A extends Array<Object>, R> extends Task
```

Implements a generic task. **GenericsTask** inherits from [Task](arkts-arkts-taskpool-task-c.md). During the creation of a generic task, the passed-in parameter types and return value types of concurrent functions are verified in the compilation phase. Other behaviors are the same as those during the creation of a task.

**Inheritance/Implementation:** GenericsTask extends [Task](arkts-arkts-taskpool-task-c.md)

**Since:** 13

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { taskpool } from '@kit.ArkTS';
```

## constructor

```TypeScript
constructor(func: (...args: A) => R | Promise<R>, ...args: A)
```

A constructor used to create a **GenericsTask** object.

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| func | (...args: A) =&gt; R &#124; Promise&lt;R&gt; | Yes | Function to be executed. The function must be decorated using [@Concurrent](../../../arkts-utils/taskpool-introduction.md#concurrent-decorator). For details about the supported return value types of the function, see [Sequenceable Data Types](../../../reference/apis-arkts/js-apis-taskpool.md#sequenceable-data-types). |
| args | A | Yes | Arguments of the function. For details about the supported parameter types, see [Sequenceable Data Types](../../../reference/apis-arkts/js-apis-taskpool.md#sequenceable-data-types). The default value is **undefined**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200014](../errorcode-utils.md#10200014-non-concurrent-function-error) | The function is not marked as concurrent. |

**Examples**

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

<a id="constructor-1"></a>

## constructor

```TypeScript
constructor(name: string, func: (...args: A) => R | Promise<R>, ...args: A)
```

A constructor used to create a **GenericsTask** instance, with the task name specified.

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the generic task. |
| func | (...args: A) =&gt; R &#124; Promise&lt;R&gt; | Yes | Function to be executed. The function must be decorated using [@Concurrent](../../../arkts-utils/taskpool-introduction.md#concurrent-decorator). For details about the supported return value types of the function, see [Sequenceable Data Types](../../../reference/apis-arkts/js-apis-taskpool.md#sequenceable-data-types). |
| args | A | Yes | Arguments of the function. For details about the supported parameter types, see [Sequenceable Data Types](../../../reference/apis-arkts/js-apis-taskpool.md#sequenceable-data-types). The default value is **undefined**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200014](../errorcode-utils.md#10200014-non-concurrent-function-error) | The function is not marked as concurrent. |

**Examples**

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
