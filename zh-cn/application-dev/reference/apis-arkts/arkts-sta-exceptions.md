# Exceptions
<!--Kit: ArkTS-->
<!--Subsystem: RuntimeCore-->
<!--Owner: @lijin1039-->
<!--Designer: @lijin1039-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @zhang_yixin13-->

本模块提供ArkTS-Sta标准库中的通用异常类型。这些类型均继承自`Error`，用于表达参数、状态、运行时和不支持操作等错误场景。

> **说明：**
>
> - 本模块仅适用于ArkTS-Sta。
>
> - `Error`基类已预置`code`字段，开发者可以继承`Error`基类自定义错误码行为。本模块中的built-in内置异常类型不会使用该`code`字段，built-in内置异常的`code`值默认为0。

## NoDataError

需要数据但未提供时抛出的错误。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### constructor

constructor(message?: String, options?: ErrorOptions)

创建`NoDataError`实例。`message`用于设置错误消息，`options.cause`可设置原始原因。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| message | String | 否 | 错误消息。 |
| options | ErrorOptions | 否 | 错误选项，通常包含错误栈信息。 |

**示例：**

```ts
// 模拟查询配置项，未找到时抛出NoDataError
function getConfig(key: string): string {
  const config: Record<string, string> = { 'host': '127.0.0.1', 'port': '8080' };
  const value = config[key];
  if (value === undefined) {
    throw new NoDataError('config not found', { cause: 'key=' + key });
  }
  return value;
}

try {
  getConfig('timeout');
} catch (e) {
  if (e instanceof NoDataError) {
    console.info(e.name);    // "NoDataError"
    console.info(e.message); // "config not found"
    console.info(e.cause);   // "key=timeout"
  }
}
```

## ArgumentOutOfRangeError

参数值超出允许范围时抛出的错误。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### constructor

constructor(message?: String, options?: ErrorOptions)

创建`ArgumentOutOfRangeError`实例。`message`用于设置错误消息，`options.cause`可设置原始原因。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| message | String | 否 | 错误消息。 |
| options | ErrorOptions | 否 | 错误选项，通常包含错误栈信息。 |

**示例：**

```ts
// 模拟按索引获取数组元素，索引越界时抛出ArgumentOutOfRangeError
function getItemAt(arr: double[], index: int): double {
  if (index < 0 || index >= arr.length) {
    throw new ArgumentOutOfRangeError('index out of range', { cause: 'index=' + index.toString() + ', length=' + arr.length.toString() });
  }
  return arr[index];
}

try {
  getItemAt([10, 20, 30], 5);
} catch (e) {
  if (e instanceof ArgumentOutOfRangeError) {
    console.info(e.name);    // "ArgumentOutOfRangeError"
    console.info(e.message); // "index out of range"
    console.info(e.cause);   // "index=5, length=3"
  }
}
```

## IllegalStateError

方法在非法或不合适的状态下被调用时抛出的错误。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### constructor

constructor(message?: String, options?: ErrorOptions)

创建`IllegalStateError`实例。`message`用于设置错误消息，`options.cause`可设置原始原因。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| message | String | 否 | 错误消息。 |
| options | ErrorOptions | 否 | 错误选项，通常包含错误栈信息。 |

**示例：**

```ts
// 模拟连接池，未连接时调用查询抛出IllegalStateError
class ConnectionPool {
  private connected: boolean = false;

  connect(): void {
    this.connected = true;
  }

  query(sql: string): string {
    if (!this.connected) {
      throw new IllegalStateError('not connected', { cause: 'ConnectionPool is disconnected' });
    }
    return 'result of ' + sql;
  }
}

const pool = new ConnectionPool();
try {
  pool.query('SELECT * FROM users');
} catch (e) {
  if (e instanceof IllegalStateError) {
    console.info(e.name);    // "IllegalStateError"
    console.info(e.message); // "not connected"
    console.info(e.cause);   // "ConnectionPool is disconnected"
  }
}
```

## UnsupportedOperationError

请求的操作不受支持时抛出的错误。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### constructor

constructor(message?: String, options?: ErrorOptions)

创建`UnsupportedOperationError`实例。`message`用于设置错误消息，`options.cause`可设置原始原因。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| message | String | 否 | 错误消息。 |
| options | ErrorOptions | 否 | 错误选项，通常包含错误栈信息。 |

**示例：**

```ts
// 模拟只读集合，调用修改方法时抛出UnsupportedOperationError
class ReadOnlyList {
  private items: double[] = [1, 2, 3];

  get(index: int): double {
    return this.items[index];
  }

  add(item: double): void {
    throw new UnsupportedOperationError('add is not supported', { cause: 'ReadOnlyList does not allow modifications' });
  }
}

const list = new ReadOnlyList();
try {
  list.add(4);
} catch (e) {
  if (e instanceof UnsupportedOperationError) {
    console.info(e.name);    // "UnsupportedOperationError"
    console.info(e.message); // "add is not supported"
    console.info(e.cause);   // "ReadOnlyList does not allow modifications"
  }
}
```

## IllegalArgumentError

方法收到非法参数时抛出的错误。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### constructor

constructor(message?: String, options?: ErrorOptions)

创建`IllegalArgumentError`实例。`message`用于设置错误消息，`options.cause`可设置原始原因。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| message | String | 否 | 错误消息。 |
| options | ErrorOptions | 否 | 错误选项，通常包含错误栈信息。 |

**示例：**

```ts
// 模拟设置重复次数，传入负数时抛出IllegalArgumentError
function setRetryCount(count: int): void {
  if (count < 0) {
    throw new IllegalArgumentError('count must be non-negative', { cause: 'count=' + count.toString() });
  }
  console.info('retry count set to ' + count.toString());
}

try {
  setRetryCount(-1);
} catch (e) {
  if (e instanceof IllegalArgumentError) {
    console.info(e.name);    // "IllegalArgumentError"
    console.info(e.message); // "count must be non-negative"
    console.info(e.cause);   // "count=-1"
  }
}
```

## RuntimeError

运行时错误的通用类型。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### constructor

constructor(message?: String, options?: ErrorOptions)

创建`RuntimeError`实例。`message`用于设置错误消息，`options.cause`可设置原始原因。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| message | String | 否 | 错误消息。 |
| options | ErrorOptions | 否 | 错误选项，通常包含错误栈信息。 |

**示例：**

```ts
// 模拟除法运算，除数为零时抛出RuntimeError
function divide(a: double, b: double): double {
  if (b === 0) {
    throw new RuntimeError('division by zero', { cause: 'divisor is zero' });
  }
  return a / b;
}

try {
  divide(10, 0);
} catch (e) {
  if (e instanceof RuntimeError) {
    console.info(e.name);    // "RuntimeError"
    console.info(e.message); // "division by zero"
    console.info(e.cause);   // "divisor is zero"
  }
}
```
