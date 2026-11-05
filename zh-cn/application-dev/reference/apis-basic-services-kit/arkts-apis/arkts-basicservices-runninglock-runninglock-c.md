# RunningLock

```TypeScript
class RunningLock
```

阻止系统睡眠或使能接近光控制亮灭屏的锁，不同的锁类型具有不同的功能，详见[RunningLockType](arkts-basicservices-runninglock-runninglocktype-e.md)。需结合[create](arkts-basicservices-runninglock-create-f.md)创建锁、[hold](#hold)持锁、[unhold](#unhold)释放锁使用。具体使用方法见示例。RunningLock 对象不可在多个 Worker/TaskPool 线程间共享。同一 RunningLock 实例的 hold()、unhold()、isHolding() 方法必须在同一线程调用，跨线程共享可能导致锁状态不一致且不报错。当电源服务异常重启后，已创建的 RunningLock 对象仍然有效，但锁的持有状态可能丢失。建议在服务重启场景下通过 isHolding() 检查锁状态，必要时重新调用 hold()。当 RunningLock 的 JS 对象被垃圾回收时，底层持有的锁会被自动释放。如需长期持锁，请保持对 RunningLock 对象的引用。

**起始版本：** 7

<!--Device-runningLock-class RunningLock--><!--Device-runningLock-class RunningLock-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

## 导入模块

```TypeScript
import { runningLock } from '@kit.BasicServicesKit';
```

## hold

```TypeScript
hold(timeout: number): void
```

锁定和持有RunningLock。适用于应用需要在后台持续运行（如后台下载、长时间定位追踪等）时阻止系统睡眠的场景或通话时需要接近光控制亮灭屏的场景等。调用此方法后，必须在使用完毕时调用unhold()释放锁，或者在调用时设置超时释放时间由系统自动释放，与unhold()方法配对使用。未释放锁会导致阻止睡眠或者控制亮灭屏功能持续生效。重复调用hold()不会报错。注意：如果先调用hold(-1)（永久持锁）再调用 hold(timeout)（定时持锁），锁将在timeout毫秒后释放，即后一次调用的超时参数会覆盖前一次。建议如需更新超时时间，先调用unhold()释放锁后再调用hold(newTimeout)。

**起始版本：** 9

**需要权限：** ohos.permission.RUNNING_LOCK

<!--Device-RunningLock-hold(timeout: int): void--><!--Device-RunningLock-hold(timeout: int): void-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timeout | number | 是 | 锁定和持有RunningLock的时长，单位：毫秒。<br>**-1**：永久持锁，需要主动释放。<br>**0**：默认3s后超时释放。<br> **&gt;0**：按传入值超时释放。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | If the permission is denied. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes: 1. Incorrect parameter types;         2. Parameter verification failed. |

**示例**

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

查询当前RunningLock是持有状态还是释放状态。

**起始版本：** 9

<!--Device-RunningLock-isHolding(): boolean--><!--Device-RunningLock-isHolding(): boolean-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示当前RunningLock是持有状态，返回false表示当前RunningLock是释放状态。 |

**示例**

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

释放RunningLock锁。此方法与hold()配对使用，在调用hold()锁定后调用此方法释放锁。对未持有的锁调用unhold()不会报错，视为无操作。

**起始版本：** 9

**需要权限：** ohos.permission.RUNNING_LOCK

<!--Device-RunningLock-unhold(): void--><!--Device-RunningLock-unhold(): void-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | If the permission is denied. |

**示例**

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

查询当前RunningLock是持有状态还是释放状态。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [isHolding](#isholding)

<!--Device-RunningLock-isUsed(): boolean--><!--Device-RunningLock-isUsed(): boolean-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示当前RunningLock是持有状态，返回false表示当前RunningLock是释放状态。 |

**示例**

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

持有RunningLock锁。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [hold](#hold)

**需要权限：** ohos.permission.RUNNING_LOCK

<!--Device-RunningLock-lock(timeout: number): void--><!--Device-RunningLock-lock(timeout: number): void-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timeout | number | 是 | 锁定和持有RunningLock的时长，单位：毫秒。 |

**示例**

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

释放RunningLock锁。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [unhold](#unhold)

**需要权限：** ohos.permission.RUNNING_LOCK

<!--Device-RunningLock-unlock(): void--><!--Device-RunningLock-unlock(): void-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**示例**

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
