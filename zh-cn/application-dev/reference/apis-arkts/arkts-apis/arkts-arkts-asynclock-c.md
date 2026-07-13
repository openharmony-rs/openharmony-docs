# AsyncLock

在锁下执行异步操作的类。

**起始版本：** 12

**装饰器类型：** @Sendable

**系统能力：** SystemCapability.Utils.Lang

## constructor

```TypeScript
constructor()
```

默认构造函数。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## lockAsync

```TypeScript
lockAsync<T>(callback: AsyncLockCallback<T>): Promise<T>
```

在获取的独占锁下执行操作。该方法首先获取锁，然后调用回调，最后释放锁。回调在调用lockAsync的同一线程中以异步方式执行。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncLockCallback&lt;T&gt; | 是 | 获取锁后要调用的函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;T&gt; | 回调执行后将解决的Promise。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200030](../errorcode-utils.md#10200030-锁不存在) | The lock does not exist. |

## lockAsync

```TypeScript
lockAsync<T>(callback: AsyncLockCallback<T>, mode: AsyncLockMode): Promise<T>
```

在获取的锁下执行操作。该方法首先获取锁，然后调用回调，最后释放锁。回调在调用lockAsync的同一线程中以异步方式执行。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncLockCallback&lt;T&gt; | 是 | 获取锁后要调用的函数。 |
| mode | AsyncLockMode | 是 | 锁的操作模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;T&gt; | 回调执行后将解决或拒绝的Promise。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200030](../errorcode-utils.md#10200030-锁不存在) | The lock does not exist. |

## lockAsync

```TypeScript
lockAsync<T, U>(callback: AsyncLockCallback<T>, mode: AsyncLockMode,
        options: AsyncLockOptions<U>): Promise<T | U>
```

在获取的锁下执行操作。该方法首先获取锁，然后调用回调，最后释放锁。回调在调用lockAsync的同一线程中以异步方式执行。
在{@link AsyncLockOptions}中可以提供一个可选的超时值。在这种情况下，如果超时前未能获取锁，lockAsync将返回被拒绝的Promise并带上一个BusinessError实例。
这种情况下，错误信息将包含持有的锁和等待的锁的信息以及可能的死锁警告。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncLockCallback&lt;T&gt; | 是 | 获取锁后要调用的函数。 |
| mode | AsyncLockMode | 是 | 锁的操作模式。 |
| options | AsyncLockOptions&lt;U&gt; | 是 | 锁的操作选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;T \| U&gt; | 回调执行后将解决的Promise，或者在超时情况下被拒绝。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200030](../errorcode-utils.md#10200030-锁不存在) | The lock does not exist. |
| [10200031](../errorcode-utils.md#10200031-lockasync超时) | Timeout exceeded. |

## query

```TypeScript
static query(name: string): AsyncLockState
```

查询指定锁的信息。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 锁的名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| AsyncLockState | 返回AsyncLockState实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200030](../errorcode-utils.md#10200030-锁不存在) | The lock does not exist. |

## queryAll

```TypeScript
static queryAll(): AsyncLockState[]
```

查询所有锁的信息。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| AsyncLockState[] | 返回AsyncLockState数组。 |

## request

```TypeScript
static request(name: string): AsyncLock
```

使用指定的名称查找或创建AsyncLock实例。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 要查找或创建的锁的名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| AsyncLock | 返回AsyncLock实例。 |

## name

```TypeScript
readonly name: string
```

锁的名称。

**类型：** string

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

