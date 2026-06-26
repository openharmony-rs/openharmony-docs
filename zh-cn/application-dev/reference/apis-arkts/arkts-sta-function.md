# Function
<!--Kit: ArkTS-->
<!--Subsystem: RuntimeCore-->
<!--Owner: @lijin1039-->
<!--Designer: @lijin1039-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @zhang_yixin13-->

本模块提供ArkTS-Sta函数对象接口和固定参数个数的函数/Lambda类型。运行时使用这些接口统一表示普通函数、闭包以及可变参数调用。

> **说明：**
>
> - 本模块仅适用于ArkTS-Sta。

## Function

export interface Function

所有函数对象的基础接口。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### unsafeCall

unsafeCall(...r: FixedArray\<Any>): Any

以运行时参数数组调用函数。由于参数类型为`FixedArray<Any>`，调用时不进行参数类型检查，因此称为"unsafe"。参数数量不足时将抛出`ArgumentsUnderapplicationError`；参数数量多于函数声明参数个数时，多余参数将被忽略。

与直接调用函数相比，`unsafeCall`适用于需要动态分发调用的场景（如回调注册、策略模式等），但由于缺乏编译期类型检查，建议在类型已知时优先使用直接调用。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| r | FixedArray\<Any> | 否 | 传递的参数列表。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Any | 函数执行结果。 |

**错误信息：**

| 错误信息 | 说明 |
| --- | --- |
| ArgumentsUnderapplicationError | 传入的参数数量少于函数声明参数个数时抛出。<br>可能原因：调用函数时传入的参数数量不足。<br>处理步骤：检查函数调用时传入的参数数量是否满足函数声明的参数个数要求。 |

**示例1：**

```ts
const add: Function = (left: int, right: int): int => left + right;

const greet: Function = (name: string): string => "Hello, " + name;

const fn: Function = (): double => 42;

function multiply(a: int, b: int): int {
    return a * b;
}

console.info(add.unsafeCall(2, 5)); // 7
console.info(greet.unsafeCall("ArkTS")); // "Hello, ArkTS"
console.info(fn.unsafeCall()); // 42
console.info(multiply.unsafeCall(3, 7)); // 21
```

**示例2：**

```ts
// 参数数量不足时抛出ArgumentsUnderapplicationError
const add: Function = (left: int, right: int): int => left + right;
try {
  add.unsafeCall(2); // 缺少第二个参数
} catch (e) {
  console.info(e instanceof ArgumentsUnderapplicationError); // true
}

// 参数数量多于函数声明参数个数时，多余参数被忽略
console.info(add.unsafeCall(2, 5, 10)); // 7
```

**示例3：**

```ts
// 闭包捕获变量
function makeCounter(): Function {
  let count: int = 0;
  const counter: Function = (): int => {
    count++;
    return count;
  };
  return counter;
}

const counter = makeCounter();
console.info(counter.unsafeCall()); // 1
console.info(counter.unsafeCall()); // 2
console.info(counter.unsafeCall()); // 3
```

### name

get name(): string

获取函数名称。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 函数名称。 |

**示例：**

```ts
const add: Function = (left: int, right: int): int => left + right;

function multiply(a: int, b: int): int {
    return a * b;
}

const anonymous: Function = () => {};

console.info(add.name); // "add"
console.info(multiply.name); // "multiply"
console.info(anonymous.name); // "anonymous"
```
