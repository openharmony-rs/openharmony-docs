# RunningLock

```TypeScript
class RunningLock
```

The lock that prevents the system from sleeping or enanles the proximity sensor to control screen on/off. Different types of locks have diffrent functions. For details, see RunningLockType. This API must be used together with [create]{@liink runninglockcreate9} to create a lock, hold to hold the lock, and unhold to release the lock. For details, see the example. A RunningLock object cannot be shared among multiple Worker or TaskPool threads. The hold(), unhold(), and isHolding() methods of the same RunningLock instance must be called in the same thread. If the methods are called in different threads, the lock status may be inconsistent and no error will be reported. After the power service restarts unexpectedly, the craeted RunningLock object is still valid, but the service restart scenario and call the hold() method again if necessary. When the JS object of a RunningLock is garbage collected, the lock held by the underlying layer is automatically released. To hold the lock for a long time, keep the reference to the RunningLock object.

**Since:** 7

<!--Device-runningLock-class RunningLock--><!--Device-runningLock-class RunningLock-End-->

**System capability:** SystemCapability.PowerManager.PowerManager.Core

## Modules to Import

```TypeScript
import { runningLock } from '@kit.BasicServicesKit';
```

## hold

```TypeScript
hold(timeout: number): void
```

Lock and hold RunningLock. This mode is applicable to scenarios where the system sleeps when apps are running continuously in the background(such as background download and long-term location tracking) or scenarios where the proximity sensor is required to turn on and off the screen during a call. When this method is called, You must call unhold() to release the lock when the use is complete, or set the timeout release time when the call is complete so that the system automatically releases the lock. This method is used together with the unhold() method. If the lock is not released, the sleep or screen control function will continue to take effect. No error is reported when hold() is called repeatedly. Note: If hold(-1) is called before hold(timeout) is called, the lock is released after timeout milliseconds. That is, the timeout parameter of the next call overwrites the previous one. To update the timeout interval, call unhold() to release the lock and then call hold(newTimeout).

**Since:** 9

**Required permissions:** ohos.permission.RUNNING_LOCK

<!--Device-RunningLock-hold(timeout: int): void--><!--Device-RunningLock-hold(timeout: int): void-End-->

**System capability:** SystemCapability.PowerManager.PowerManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| timeout | number | Yes | Duration for locking and holding the **RunningLock** object, in ms.<br>The value must be a number:<br>**-1**: The lock is permanently held and needs to be released automatically.<br>**0**: The lock is released 3 seconds after the timer expires by default.<br>   > 0: The lock is released based on the input value after the timer expires. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | If the permission is denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types;         2. Parameter verification failed. |

**Examples**

```TypeScript
// RunningLockTest.ets
class RunningLockTest {
    public static recordLock: runningLock.RunningLock;

    public static holdRunningLock(): void {
        if (RunningLockTest.recordLock) {
            try {
                RunningLockTest.recordLock.hold(500);
                console.info('hold running lock success');
            } catch(err) {
                console.error(`Failed to hold running lock. Code: ${err.code}, message: ${err.message}`);
            }
        } else {
            runningLock.create('running_lock_test', runningLock.RunningLockType.PROXIMITY_SCREEN_CONTROL, (err: BusinessError, lock: runningLock.RunningLock) => {
                if (err) {
                    console.error(`Failed to create running lock. Code: ${err.code}, message: ${err.message}`);
                } else {
                    console.info('create running lock: ' + lock);
                    RunningLockTest.recordLock = lock;
                    try {
                        lock.hold(500);
                        console.info('hold running lock success');
                    } catch(err) {
                        console.error(`Failed to hold running lock. Code: ${err.code}, message: ${err.message}`);
                    }
                }
            });
        }
    }
}
```

## isHolding

```TypeScript
isHolding(): boolean
```

Checks whether this running lock is being held.

**Since:** 9

<!--Device-RunningLock-isHolding(): boolean--><!--Device-RunningLock-isHolding(): boolean-End-->

**System capability:** SystemCapability.PowerManager.PowerManager.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | The value **true** indicates that the **RunningLock** object is held; and the value **false** indicates that the **RunningLock** object is released. |

**Examples**

```TypeScript
// RunningLockTest.ets
class RunningLockTest {
    public static recordLock: runningLock.RunningLock;

    public static isHoldingRunningLock(): void {
        if (RunningLockTest.recordLock) {
            let isHolding = RunningLockTest.recordLock.isHolding();
            console.info('check running lock holding status: ' + isHolding);
        } else {
            runningLock.create('running_lock_test', runningLock.RunningLockType.PROXIMITY_SCREEN_CONTROL, (err: BusinessError, lock: runningLock.RunningLock) => {
                if (err) {
                    console.error(`Failed to create running lock. Code: ${err.code}, message: ${err.message}`);
                } else {
                    console.info('create running lock: ' + lock);
                    RunningLockTest.recordLock = lock;
                    let isHolding = lock.isHolding();
                    console.info('check running lock holding status: ' + isHolding);
                }
            });
        }
    }
}
```

## unhold

```TypeScript
unhold(): void
```

Release the RunningLock lock. This method is used in conjunction with hold() to release the lock after holding() is called. Calling unhold() on an unheld lock does not report an error and is considered as no operation.

**Since:** 9

**Required permissions:** ohos.permission.RUNNING_LOCK

<!--Device-RunningLock-unhold(): void--><!--Device-RunningLock-unhold(): void-End-->

**System capability:** SystemCapability.PowerManager.PowerManager.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | If the permission is denied. |

**Examples**

```TypeScript
// RunningLockTest.ets
class RunningLockTest {
    public static recordLock: runningLock.RunningLock;

    public static unholdRunningLock(): void {
        if (RunningLockTest.recordLock) {
            try {
                RunningLockTest.recordLock.unhold();
                console.info('unhold running lock success');
            } catch(err) {
                console.error(`Failed to unhold running lock. Code: ${err.code}, message: ${err.message}`);
            }
        } else {
            runningLock.create('running_lock_test', runningLock.RunningLockType.PROXIMITY_SCREEN_CONTROL, (err: BusinessError, lock: runningLock.RunningLock) => {
                if (err) {
                    console.error(`Failed to create running lock. Code: ${err.code}, message: ${err.message}`);
                } else {
                    console.info('create running lock: ' + lock);
                    RunningLockTest.recordLock = lock;
                    try {
                        lock.unhold();
                        console.info('unhold running lock success');
                    } catch(err) {
                        console.error(`Failed to unhold running lock. Code: ${err.code}, message: ${err.message}`);
                    }
                }
            });
        }
    }
}
```

## isUsed

```TypeScript
isUsed(): boolean
```

Checks whether this running lock is used.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [isHolding](#isholding)

<!--Device-RunningLock-isUsed(): boolean--><!--Device-RunningLock-isUsed(): boolean-End-->

**System capability:** SystemCapability.PowerManager.PowerManager.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns true if the lock is held or in use; returns false if the lock has been released. |

**Examples**

```TypeScript
runningLock.createRunningLock('running_lock_test', runningLock.RunningLockType.BACKGROUND)
.then((lock: runningLock.RunningLock) => {
    let isUsed = lock.isUsed();
    console.info('check running lock used status: ' + isUsed);
})
.catch((err: BusinessError) => {
    console.error(`Failed to check running lock used status. Code: ${err.code}, message: ${err.message}`);
});
```

## lock

```TypeScript
lock(timeout: number): void
```

Locks and holds a **RunningLock** object.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [hold](#hold)

**Required permissions:** ohos.permission.RUNNING_LOCK

<!--Device-RunningLock-lock(timeout: number): void--><!--Device-RunningLock-lock(timeout: number): void-End-->

**System capability:** SystemCapability.PowerManager.PowerManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| timeout | number | Yes | Duration for locking and holding the **RunningLock** object, in ms. |

**Examples**

```TypeScript
runningLock.createRunningLock('running_lock_test', runningLock.RunningLockType.BACKGROUND)
.then((lock: runningLock.RunningLock) => {
    lock.lock(500);
    console.info('create running lock and lock success');
})
.catch((err: BusinessError) => {
    console.error(`Failed to create running lock. Code: ${err.code}, message: ${err.message}`);
});
```

## unlock

```TypeScript
unlock(): void
```

Releases this running lock.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [unhold](#unhold)

**Required permissions:** ohos.permission.RUNNING_LOCK

<!--Device-RunningLock-unlock(): void--><!--Device-RunningLock-unlock(): void-End-->

**System capability:** SystemCapability.PowerManager.PowerManager.Core

**Examples**

```TypeScript
runningLock.createRunningLock('running_lock_test', runningLock.RunningLockType.BACKGROUND)
.then((lock: runningLock.RunningLock) => {
    lock.unlock();
    console.info('create running lock and unlock success');
})
.catch((err: BusinessError) => {
    console.error(`Failed to create running lock. Code: ${err.code}, message: ${err.message}`);
});
```
