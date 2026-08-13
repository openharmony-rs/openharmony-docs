# RunningLock

阻止系统睡眠的锁。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-runningLock-class RunningLock--><!--Device-runningLock-class RunningLock-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

## hold

```TypeScript
hold(timeout: int): void
```

锁定和持有RunningLock。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.RUNNING_LOCK

<!--Device-RunningLock-hold(timeout: int): void--><!--Device-RunningLock-hold(timeout: int): void-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timeout | int | 是 | 锁定和持有RunningLock的时长，单位：毫秒。&lt;br&gt;该参数必须为数字类型：&lt;br&gt;**-1**：永久持锁，需要主动释放。&lt;br&gt;**0**：默认3s后超时释放。&lt;br&gt; **>0**：按传入值超时释放。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Incorrect parameter types; |
| [201](../../errorcode-universal.md#201-权限校验失败) | If the permission is denied. |

## 示例

```TypeScript
// RunningLockTest.ets
class RunningLockTest {
    public static recordLock: runningLock.RunningLock | undefined;

    public static holdRunningLock(): void {
        if (RunningLockTest.recordLock) {
            RunningLockTest.recordLock!.hold(500);
            console.info('hold running lock success');
        } else {
            runningLock.create('running_lock_test', runningLock.RunningLockType.PROXIMITY_SCREEN_CONTROL, (err: Error | null, lock: runningLock.RunningLock | undefined) => {
                if (!err) {
                    console.info('create running lock: ' + lock);
                    RunningLockTest.recordLock = lock!;
                    try {
                        lock!.hold(500);
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

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-RunningLock-isHolding(): boolean--><!--Device-RunningLock-isHolding(): boolean-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示当前RunningLock是持有状态，返回false表示当前RunningLock是释放状态。 |

## 示例

```TypeScript
// RunningLockTest.ets
class RunningLockTest {
    public static recordLock: runningLock.RunningLock | undefined;

    public static isHoldingRunningLock(): void {
        if (RunningLockTest.recordLock) {
            let isHolding = RunningLockTest.recordLock!.isHolding();
            console.info('check running lock holding status: ' + isHolding);
        } else {
            runningLock.create('running_lock_test', runningLock.RunningLockType.PROXIMITY_SCREEN_CONTROL, (err: Error | null, lock: runningLock.RunningLock | undefined) => {
                if (!err) {
                    console.info('create running lock: ' + lock);
                    RunningLockTest.recordLock = lock!;
                    let isHolding = lock!.isHolding();
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

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [isHolding](#isHolding)

<!--Device-RunningLock-isUsed(): boolean--><!--Device-RunningLock-isUsed(): boolean-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示当前RunningLock是持有状态，返回false表示当前RunningLock是释放状态。 |

## 示例

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

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [hold](#hold)

**需要权限：** ohos.permission.RUNNING_LOCK

<!--Device-RunningLock-lock(timeout: number): void--><!--Device-RunningLock-lock(timeout: number): void-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timeout | number | 是 | 锁定和持有RunningLock的时长，单位：毫秒。 |

## 示例

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

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.RUNNING_LOCK

<!--Device-RunningLock-unhold(): void--><!--Device-RunningLock-unhold(): void-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | If the permission is denied. |

## 示例

```TypeScript
// RunningLockTest.ets
class RunningLockTest {
    public static recordLock: runningLock.RunningLock | undefined;

    public static unholdRunningLock(): void {
        if (RunningLockTest.recordLock) {
            RunningLockTest.recordLock!.unhold();
            console.info('unhold running lock success');
        } else {
            runningLock.create('running_lock_test', runningLock.RunningLockType.PROXIMITY_SCREEN_CONTROL, (err: Error | null, lock: runningLock.RunningLock | undefined) => {
                if (!err) {
                    console.info('create running lock: ' + lock);
                    RunningLockTest.recordLock = lock!;
                    try {
                        lock!.hold(500);
                        // Finish other tasks before unhold lock.
                        lock!.unhold();
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

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [unhold](#unhold)

**需要权限：** ohos.permission.RUNNING_LOCK

<!--Device-RunningLock-unlock(): void--><!--Device-RunningLock-unlock(): void-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

## 示例

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

