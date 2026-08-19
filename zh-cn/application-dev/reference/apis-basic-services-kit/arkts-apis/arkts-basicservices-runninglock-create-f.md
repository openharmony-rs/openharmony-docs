# create

## 导入模块

```TypeScript
import { runningLock } from '@kit.BasicServicesKit';
```

## create

```TypeScript
function create(name: string, type: RunningLockType, callback: AsyncCallback<RunningLock>): void
```

创建RunningLock锁对象。使用callback异步回调。创建锁对象后，需调用hold()方法锁定和持有该锁，才能使锁功能生效。

**起始版本：** 23

**需要权限：** ohos.permission.RUNNING_LOCK

<!--Device-runningLock-function create(name: string, type: RunningLockType, callback: AsyncCallback<RunningLock>): void--><!--Device-runningLock-function create(name: string, type: RunningLockType, callback: AsyncCallback<RunningLock>): void-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 锁的名字。建议使用包名或类名加后缀的方式命名。 |
| type | [RunningLockType](arkts-basicservices-runninglock-runninglocktype-e.md) | 是 | 要创建的锁的类型。不同锁类型有不同的使用注意事项，详见RunningLockType。 |
| callback | [AsyncCallback](arkts-basicservices-asynccallback-t.md)&lt;[RunningLock](arkts-basicservices-runninglock-runninglock-c.md)&gt; | 是 | 回调函数。当创建锁成功，err为undefined，data为创建的RunningLock；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | If the permission is denied. |

**示例**

ArkTS-Dyn示例：

```TypeScript
runningLock.create('running_lock_test', runningLock.RunningLockType.PROXIMITY_SCREEN_CONTROL, (err: Error, lock: runningLock.RunningLock) => {
    if (typeof err === 'undefined') {
        console.info('created running lock: ' + lock);
    } else {
        console.error('create running lock failed, err: ' + err);
    }
});
```

ArkTS-Sta示例：

```TypeScript
runningLock.create('running_lock_test', runningLock.RunningLockType.PROXIMITY_SCREEN_CONTROL, (err: Error | null, lock: runningLock.RunningLock | undefined) => {
    if (!err) {
        console.info('created running lock: ' + lock);
    } else {
        console.error('create running lock failed, err: ' + err);
    }
});
```


## create

```TypeScript
function create(name: string, type: RunningLockType): Promise<RunningLock>
```

创建RunningLock锁对象。使用Promise异步回调。创建锁对象后，需调用hold()方法锁定和持有该锁，才能使锁功能生效。

**起始版本：** 23

**需要权限：** ohos.permission.RUNNING_LOCK

<!--Device-runningLock-function create(name: string, type: RunningLockType): Promise<RunningLock>--><!--Device-runningLock-function create(name: string, type: RunningLockType): Promise<RunningLock>-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 锁的名字。建议使用包名或类名加后缀的方式命名。 |
| type | [RunningLockType](arkts-basicservices-runninglock-runninglocktype-e.md) | 是 | 要创建的锁的类型。不同锁类型有不同的使用注意事项，详见RunningLockType。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[RunningLock](arkts-basicservices-runninglock-runninglock-c.md)&gt; | Promise对象。创建成功时返回RunningLock锁对象；创建失败时返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | If the permission is denied. |

**示例**

```TypeScript
runningLock.create('running_lock_test', runningLock.RunningLockType.PROXIMITY_SCREEN_CONTROL)
.then((lock: runningLock.RunningLock) => {
    console.info('created running lock: ' + lock);
})
.catch((err: Error) => {
    console.error('create running lock failed, err: ' + err);
});
```

