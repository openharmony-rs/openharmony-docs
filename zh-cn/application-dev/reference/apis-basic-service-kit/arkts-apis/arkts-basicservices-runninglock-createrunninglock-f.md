# createRunningLock

## createRunningLock

```TypeScript
function createRunningLock(name: string, type: RunningLockType, callback: AsyncCallback<RunningLock>): void
```

创建RunningLock锁。使用callback异步回调。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [runningLock.create](arkts-basicservices-runninglock-create-f.md#create)

**需要权限：** ohos.permission.RUNNING_LOCK

<!--Device-runningLock-function createRunningLock(name: string, type: RunningLockType, callback: AsyncCallback<RunningLock>): void--><!--Device-runningLock-function createRunningLock(name: string, type: RunningLockType, callback: AsyncCallback<RunningLock>): void-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 锁的名字。建议使用包名或类名加后缀的方式命名。 |
| type | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 要创建的锁的类型。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;RunningLock&gt; | 是 | 回调函数。当创建锁成功，err为undefined，data为创建的RunningLock；否则为错误对象；AsyncCallback封装了一个RunningLock类型的类。 |

**示例：**

```TypeScript
runningLock.createRunningLock('running_lock_test', runningLock.RunningLockType.BACKGROUND, (err: Error, lock: runningLock.RunningLock) => {
    if (typeof err === 'undefined') {
        console.info('created running lock: ' + lock);
    } else {
        console.error('create running lock failed, err: ' + err);
    }
});
```


## createRunningLock

```TypeScript
function createRunningLock(name: string, type: RunningLockType): Promise<RunningLock>
```

创建RunningLock锁。使用Promise异步回调。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [runningLock.create](arkts-basicservices-runninglock-create-f.md#create)

**需要权限：** ohos.permission.RUNNING_LOCK

<!--Device-runningLock-function createRunningLock(name: string, type: RunningLockType): Promise<RunningLock>--><!--Device-runningLock-function createRunningLock(name: string, type: RunningLockType): Promise<RunningLock>-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 锁的名字。建议使用包名或类名加后缀的方式命名。 |
| type | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 要创建的锁的类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;RunningLock&gt; | Promise对象，返回RunningLock锁对象。 |

**示例：**

```TypeScript
runningLock.createRunningLock('running_lock_test', runningLock.RunningLockType.BACKGROUND)
.then((lock: runningLock.RunningLock) => {
    console.info('created running lock: ' + lock);
})
.catch((err: Error) => {
    console.error('create running lock failed, err: ' + err);
});
```

