# RunningLock

阻止系统睡眠的锁。

**起始版本：** 7

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

## hold

```TypeScript
hold(timeout: number): void
```

锁定和持有RunningLock。

**起始版本：** 9

**需要权限：** ohos.permission.RUNNING_LOCK

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timeout | number | 是 | 锁定和持有RunningLock的时长，单位：毫秒。<br>该参数必须为数字类型：<br>**-1**：永久持锁，需要主动释放。<br>**0**：默认3s后超时释放。<br>**&gt;0**：按传入值超时释放。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | If the permission is denied. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Incorrect parameter types; |

**示例：**

```TypeScript
// RunningLockTest.ets
class RunningLockTest {
    public static recordLock: runningLock.RunningLock;

    public static holdRunningLock(): void {
        if (RunningLockTest.recordLock) {
            RunningLockTest.recordLock.hold(500);
            console.info('hold running lock success');
        } else {
            runningLock.create('running_lock_test', runningLock.RunningLockType.PROXIMITY_SCREEN_CONTROL, (err: Error, lock: runningLock.RunningLock) => {
                if (typeof err === 'undefined') {
                    console.info('create running lock: ' + lock);
                    RunningLockTest.recordLock = lock;
                    try {
                        lock.hold(500);
                        console.info('hold running lock success');
                    } catch(err) {
                        console.error('hold running lock failed, err: ' + err);
                    }
                } else {
                    console.error('create running lock failed, err: ' + err);
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

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示当前RunningLock是持有状态，返回false表示当前RunningLock是释放状态。 |

**示例：**

```TypeScript
// RunningLockTest.ets
class RunningLockTest {
    public static recordLock: runningLock.RunningLock;

    public static isHoldingRunningLock(): void {
        if (RunningLockTest.recordLock) {
            let isHolding = RunningLockTest.recordLock.isHolding();
            console.info('check running lock holding status: ' + isHolding);
        } else {
            runningLock.create('running_lock_test', runningLock.RunningLockType.PROXIMITY_SCREEN_CONTROL, (err: Error, lock: runningLock.RunningLock) => {
                if (typeof err === 'undefined') {
                    console.info('create running lock: ' + lock);
                    RunningLockTest.recordLock = lock;
                    let isHolding = lock.isHolding();
                    console.info('check running lock holding status: ' + isHolding);
                } else {
                    console.error('create running lock failed, err: ' + err);
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

**替代接口：** [isHolding](arkts-basicservices-runninglock-c.md#isholding-1)

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示当前RunningLock是持有状态，返回false表示当前RunningLock是释放状态。 |

**示例：**

```TypeScript
runningLock.createRunningLock('running_lock_test', runningLock.RunningLockType.BACKGROUND)
.then((lock: runningLock.RunningLock) => {
    let isUsed = lock.isUsed();
    console.info('check running lock used status: ' + isUsed);
})
.catch((err: Error) => {
    console.error('check running lock used status failed, err: ' + err);
});

```

## lock

```TypeScript
lock(timeout: number): void
```

锁定和持有RunningLock。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [hold](arkts-basicservices-runninglock-c.md#hold-1)

**需要权限：** ohos.permission.RUNNING_LOCK

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timeout | number | 是 | 锁定和持有RunningLock的时长，单位：毫秒。 |

**示例：**

```TypeScript
runningLock.createRunningLock('running_lock_test', runningLock.RunningLockType.BACKGROUND)
.then((lock: runningLock.RunningLock) => {
    lock.lock(500);
    console.info('create running lock and lock success');
})
.catch((err: Error) => {
    console.error('create running lock failed, err: ' + err);
});

```

## unhold

```TypeScript
unhold(): void
```

释放RunningLock锁。

**起始版本：** 9

**需要权限：** ohos.permission.RUNNING_LOCK

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | If the permission is denied. |

**示例：**

```TypeScript
// RunningLockTest.ets
class RunningLockTest {
    public static recordLock: runningLock.RunningLock;

    public static unholdRunningLock(): void {
        if (RunningLockTest.recordLock) {
            RunningLockTest.recordLock.unhold();
            console.info('unhold running lock success');
        } else {
            runningLock.create('running_lock_test', runningLock.RunningLockType.PROXIMITY_SCREEN_CONTROL, (err: Error, lock: runningLock.RunningLock) => {
                if (typeof err === 'undefined') {
                    console.info('create running lock: ' + lock);
                    RunningLockTest.recordLock = lock;
                    try {
                        lock.unhold();
                        console.info('unhold running lock success');
                    } catch(err) {
                        console.error('unhold running lock failed, err: ' + err);
                    }
                } else {
                    console.error('create running lock failed, err: ' + err);
                }
            });
        }
    }
}

```

## unlock

```TypeScript
unlock(): void
```

释放RunningLock锁。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [unhold](arkts-basicservices-runninglock-c.md#unhold-1)

**需要权限：** ohos.permission.RUNNING_LOCK

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**示例：**

```TypeScript
runningLock.createRunningLock('running_lock_test', runningLock.RunningLockType.BACKGROUND)
.then((lock: runningLock.RunningLock) => {
    lock.unlock();
    console.info('create running lock and unlock success');
})
.catch((err: Error) => {
    console.error('create running lock failed, err: ' + err);
});

```

