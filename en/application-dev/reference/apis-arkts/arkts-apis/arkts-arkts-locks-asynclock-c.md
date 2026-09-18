# AsyncLock

Class to execute an asynchronous operation under lock.

**Since:** 12

**Decorator:** @Sendable

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { ArkTSUtils } from '@kit.ArkTS';
```

## constructor

```TypeScript
constructor()
```

Default constructor.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## lockAsync

```TypeScript
lockAsync<T>(callback: AsyncLockCallback<T>): Promise<T>
```

Perform an operation with the acquired lock exclusively. The method acquires the lock first, then calls the callback, and then releases the lock. The callback is called asynchronously in the same thread where lockAsync was called.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncLockCallback](arkts-arkts-locks-asynclockcallback-t.md)&lt;T&gt; | Yes | function to call when the lock gets acquired. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;T&gt; | Promise that will be resolved after the callback gets executed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200030](../errorcode-utils.md#10200030-lock-does-not-exist) | The lock does not exist. |

## lockAsync

```TypeScript
lockAsync<T>(callback: AsyncLockCallback<T>, mode: AsyncLockMode): Promise<T>
```

Perform an operation with the acquired lock. The method acquires the lock first, then calls the callback, and then releases the lock. The callback is called asynchronously in the same thread where lockAsync was called.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncLockCallback](arkts-arkts-locks-asynclockcallback-t.md)&lt;T&gt; | Yes | function to call when the lock gets acquired. |
| mode | [AsyncLockMode](arkts-arkts-locks-asynclockmode-e.md) | Yes | mode of the lock operation. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;T&gt; | Promise that will be resolved after the callback gets executed or rejected. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200030](../errorcode-utils.md#10200030-lock-does-not-exist) | The lock does not exist. |

## lockAsync

```TypeScript
lockAsync<T, U>(callback: AsyncLockCallback<T>, mode: AsyncLockMode,
        options: AsyncLockOptions<U>): Promise<T | U>
```

Perform an operation with the acquired lock. The method acquires the lock first, then calls the callback, and then releases the lock. The callback is called asynchronously in the same thread where lockAsync was called. An optional timeout value can be provided in [AsyncLockOptions](arkts-arkts-locks-asynclockoptions-c.md). In this case, lockAsync will reject the resulting promise with a BusinessError instance if the lock is not acquired before timeout exceeds. The error message, in this case, will contain the held and waited locks information and possible deadlock warnings.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncLockCallback](arkts-arkts-locks-asynclockcallback-t.md)&lt;T&gt; | Yes | function to call when the lock gets acquired. |
| mode | [AsyncLockMode](arkts-arkts-locks-asynclockmode-e.md) | Yes | mode of the lock operation. |
| options | [AsyncLockOptions](arkts-arkts-locks-asynclockoptions-c.md)&lt;U&gt; | Yes | lock operation options. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;T &#124; U&gt; | Promise that will be resolved after the callback gets executed or rejected in case timeout exceeded. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200030](../errorcode-utils.md#10200030-lock-does-not-exist) | The lock does not exist. |
| [10200031](../errorcode-utils.md#10200031-calling-lockasync-timed-out) | Timeout exceeded. |

## query

```TypeScript
static query(name: string): AsyncLockState
```

Query information about the specified lock.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | name of the lock. |

**Return value:**

| Type | Description |
| --- | --- |
| [AsyncLockState](arkts-arkts-locks-asynclockstate-c.md) | Returns an instance of AsyncLockState. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200030](../errorcode-utils.md#10200030-lock-does-not-exist) | The lock does not exist. |

## queryAll

```TypeScript
static queryAll(): AsyncLockState[]
```

Query information about all locks.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [AsyncLockState](arkts-arkts-locks-asynclockstate-c.md)[] | Returns an array of AsyncLockState. |

## request

```TypeScript
static request(name: string): AsyncLock
```

Find or create an instance of AsyncLock using the specified name.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | name of the lock to find or create. |

**Return value:**

| Type | Description |
| --- | --- |
| [AsyncLock](arkts-arkts-locks-asynclock-c.md) | Returns an instance of AsyncLock. |

## name

```TypeScript
readonly name: string
```

Name of the lock.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang
