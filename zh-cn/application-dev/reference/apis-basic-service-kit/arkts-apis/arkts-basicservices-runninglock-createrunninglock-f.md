# createRunningLock

## 导入模块

```TypeScript
import { runningLock } from '@kit.BasicServicesKit';
```

## createRunningLock

```TypeScript
function createRunningLock(name: string, type: RunningLockType, callback: AsyncCallback<RunningLock>): void
```

创建RunningLock锁。使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [create](arkts-basicservices-runninglock-create-f.md#create)

**需要权限：** ohos.permission.RUNNING_LOCK

<!--Device-runningLock-function createRunningLock(name: string, type: RunningLockType, callback: AsyncCallback<RunningLock>): void--><!--Device-runningLock-function createRunningLock(name: string, type: RunningLockType, callback: AsyncCallback<RunningLock>): void-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 锁的名字。建议使用包名或类名加后缀的方式命名。 |
| type | [RunningLockType](arkts-basicservices-runninglock-runninglocktype-e.md) | 是 | 要创建的锁的类型。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;RunningLock&gt; | 是 | 回调函数。当创建锁成功，err为undefined，data为创建的RunningLock；否则为错误对象；AsyncCallback封装了一个RunningLock类型的类。 |

**示例：**

```TypeScript
runningLock.createRunningLock('running_lock_test', runningLock.RunningLockType.BACKGROUND, (err: BusinessError, lock: runningLock.RunningLock) => {
    if (err) {
        console.error(`Failed to create running lock. Code: ${err.code}, message: ${err.message}`);
    } else {
        console.info('created running lock: ' + lock);
    }
});

```


## createRunningLock

```TypeScript
function createRunningLock(name: string, type: RunningLockType): Promise<RunningLock>
```

创建RunningLock锁。使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [create](arkts-basicservices-runninglock-create-f.md#create)

**需要权限：** ohos.permission.RUNNING_LOCK

<!--Device-runningLock-function createRunningLock(name: string, type: RunningLockType): Promise<RunningLock>--><!--Device-runningLock-function createRunningLock(name: string, type: RunningLockType): Promise<RunningLock>-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 锁的名字。建议使用包名或类名加后缀的方式命名。 |
| type | [RunningLockType](arkts-basicservices-runninglock-runninglocktype-e.md) | 是 | 要创建的锁的类型。 |

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
.catch((err: BusinessError) => {
    console.error(`Failed to create running lock. Code: ${err.code}, message: ${err.message}`);
});

```

