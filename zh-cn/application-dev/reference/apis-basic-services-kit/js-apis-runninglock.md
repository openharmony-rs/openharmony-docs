# @ohos.runningLock (RunningLock锁)

<!--Kit: Basic Services Kit-->
<!--Subsystem: PowerManager-->
<!--Owner: @zhang-yinglie; @volcano_wang-->
<!--Designer: @wangyantian0-->
<!--Tester: @alien0208-->
<!--Adviser: @fang-jinxu-->

该模块为RunningLock锁相关操作的接口，提供阻止系统睡眠和使能接近光控制亮灭屏的能力，适用于设备灭屏后保持后台任务持续运行、接近光控制亮灭屏、以及阻止系统闲时自动睡眠等场景，保证关键任务的持续执行。包括创建、查询、持锁、释放锁等操作，类型详情见[RunningLockType](#runninglocktype)。

> **说明：**
>
> 本模块首批接口从 API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```js
import {runningLock} from '@kit.BasicServicesKit';
```

## runningLock.isSupported<sup>9+</sup>

isSupported(type: RunningLockType): boolean

查询系统是否支持该类型的锁。

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**参数：**

| 参数名 | 类型                                | 必填 | 说明                 |
| ------ | ----------------------------------- | ---- | -------------------- |
| type   | [RunningLockType](#runninglocktype) | 是   | 需要查询的锁的类型。 |

**返回值：**

| 类型    | 说明                                    |
| ------- | --------------------------------------- |
| boolean | 返回true表示支持，返回false表示不支持。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID   | 错误信息    |
|---------|---------|
| 401     | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |

**示例：**

```js
try {
    let isSupported = runningLock.isSupported(runningLock.RunningLockType.PROXIMITY_SCREEN_CONTROL);
    console.info('PROXIMITY_SCREEN_CONTROL type supported: ' + isSupported);
} catch (err) {
    console.error(`Failed to check supported. Code: ${err.code}, message: ${err.message}`);
}
```

## runningLock.create<sup>9+</sup>

create(name: string, type: RunningLockType, callback: AsyncCallback&lt;RunningLock&gt;): void

创建RunningLock锁对象。使用callback异步回调。创建锁对象后，需调用hold()方法锁定和持有该锁，才能使锁功能生效。

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**需要权限：** ohos.permission.RUNNING_LOCK

**参数：**

| 参数名   | 类型                                       | 必填 | 说明                                                         |
| -------- | ------------------------------------------ | ---- | ------------------------------------------------------------ |
| name     | string                                     | 是   | 锁的名字。建议使用包名或类名加后缀的方式命名。                                                   |
| type | [RunningLockType](#runninglocktype) | 是 | 要创建的锁的类型。不同锁类型有不同的使用注意事项，详见[RunningLockType](#runninglocktype)。 |
| callback | AsyncCallback<[RunningLock](#runninglock)> | 是   | 回调函数。当创建锁成功，err为undefined，data为创建的RunningLock；否则为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID   | 错误信息    |
|---------|---------|
| 401     | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |
| 201     | If the permission is denied.|

**示例：**

```js

runningLock.create('running_lock_test', runningLock.RunningLockType.PROXIMITY_SCREEN_CONTROL, (err: BusinessError, lock: runningLock.RunningLock) => {
    if (err) {
        console.error(`Failed to create running lock. Code: ${err.code}, message: ${err.message}`);
    } else {
        console.info('created running lock: ' + lock); // 创建并保存锁对象后，需要结合hold、unhold方法使用
    }
});
```

## runningLock.create<sup>9+</sup>

create(name: string, type: RunningLockType): Promise&lt;RunningLock&gt;

创建RunningLock锁对象。使用Promise异步回调。创建锁对象后，需调用hold()方法锁定和持有该锁，才能使锁功能生效。

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**需要权限：** ohos.permission.RUNNING_LOCK

**参数：**

| 参数名 | 类型                                | 必填 | 说明               |
| ------ | ----------------------------------- | ---- | ------------------ |
| name   | string                              | 是   | 锁的名字。建议使用包名或类名加后缀的方式命名。 |
| type | [RunningLockType](#runninglocktype) | 是 | 要创建的锁的类型。不同锁类型有不同的使用注意事项，详见[RunningLockType](#runninglocktype)。 |


**返回值：**

| 类型                                       | 说明                                 |
| ------------------------------------------ | ------------------------------------ |
| Promise&lt;[RunningLock](#runninglock)&gt; | Promise对象。创建成功时返回RunningLock锁对象；创建失败时返回错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID   | 错误信息    |
|---------|---------|
| 401     | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |
| 201     | If the permission is denied.|

**示例：**

```js

runningLock.create('running_lock_test', runningLock.RunningLockType.PROXIMITY_SCREEN_CONTROL)
.then((lock: runningLock.RunningLock) => {
    console.info('created running lock: ' + lock); // 创建并保存锁对象后，需要结合hold、unhold方法使用
})
.catch((err: BusinessError) => {
    console.error(`Failed to create running lock. Code: ${err.code}, message: ${err.message}`);
});
```

## runningLock.isRunningLockTypeSupported<sup>(deprecated)</sup>

isRunningLockTypeSupported(type: RunningLockType, callback: AsyncCallback&lt;boolean&gt;): void

查询系统是否支持该类型的锁。使用callback异步回调。

> **说明：**<br>从 API version 7开始支持，从 API version 9开始废弃。建议使用[runningLock.isSupported](#runninglockissupported9)替代。

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**参数：**

| 参数名   | 类型                                | 必填 | 说明                                                         |
| -------- | ----------------------------------- | ---- | ------------------------------------------------------------ |
| type     | [RunningLockType](#runninglocktype) | 是   | 需要查询的锁的类型。|
| callback | AsyncCallback&lt;boolean&gt;        | 是   | 回调函数。当查询成功，err为undefined，data为获取到的支持情况，返回true表示支持，返回false表示不支持；否则为错误对象。 |

**示例：**

```js
runningLock.isRunningLockTypeSupported(runningLock.RunningLockType.BACKGROUND, (err: BusinessError, data: boolean) => {
    if (err) {
        console.error(`Failed to check BACKGROUND lock support status. Code: ${err.code}, message: ${err.message}`);
    } else {
        console.info('BACKGROUND lock support status: ' + data);
    }
});
```

## runningLock.isRunningLockTypeSupported<sup>(deprecated)</sup>

isRunningLockTypeSupported(type: RunningLockType): Promise&lt;boolean>

查询系统是否支持该类型的锁。使用Promise异步回调。

> **说明：**<br>从 API version 7开始支持，从 API version 9开始废弃。建议使用[runningLock.isSupported](#runninglockissupported9)替代。

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**参数：**

| 参数名 | 类型                                | 必填 | 说明                 |
| ------ | ----------------------------------- | ---- | -------------------- |
| type   | [RunningLockType](#runninglocktype) | 是   | 需要查询的锁的类型。 |

**返回值：**

| 类型                   | 说明                                                 |
| ---------------------- | ---------------------------------------------------- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示支持；返回false表示不支持。 |

**示例：**

```js
runningLock.isRunningLockTypeSupported(runningLock.RunningLockType.BACKGROUND)
.then((data: boolean) => {
    console.info('BACKGROUND lock support status: ' + data);
})
.catch((err: BusinessError) => {
    console.error(`Failed to check BACKGROUND lock support status. Code: ${err.code}, message: ${err.message}`);
});
```

## runningLock.createRunningLock<sup>(deprecated)</sup>

createRunningLock(name: string, type: RunningLockType, callback: AsyncCallback&lt;RunningLock&gt;): void

创建RunningLock锁。使用callback异步回调。

> **说明：**<br>从 API version 7开始支持，从 API version 9开始废弃。建议使用[runningLock.create](#runninglockcreate9)替代。

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**需要权限：** ohos.permission.RUNNING_LOCK

**参数：**

| 参数名   | 类型                                       | 必填 | 说明                                                         |
| -------- | ------------------------------------------ | ---- | ------------------------------------------------------------ |
| name     | string                                     | 是   | 锁的名字。建议使用包名或类名加后缀的方式命名。                   |
| type     | [RunningLockType](#runninglocktype)        | 是   | 要创建的锁的类型。                                           |
| callback | AsyncCallback&lt;[RunningLock](#runninglock)&gt; | 是 | 回调函数。当创建锁成功，err为undefined，data为创建的RunningLock；否则为错误对象。 |

**示例：**

```js
runningLock.createRunningLock('running_lock_test', runningLock.RunningLockType.BACKGROUND, (err: BusinessError, lock: runningLock.RunningLock) => {
    if (err) {
        console.error(`Failed to create running lock. Code: ${err.code}, message: ${err.message}`);
    } else {
        console.info('created running lock: ' + lock);
    }
});
```

## runningLock.createRunningLock<sup>(deprecated)</sup>

createRunningLock(name: string, type: RunningLockType): Promise&lt;RunningLock&gt;

创建RunningLock锁。使用Promise异步回调。

> **说明：**<br>从 API version 7开始支持，从 API version 9开始废弃。建议使用[runningLock.create](#runninglockcreate9)替代。

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**需要权限：** ohos.permission.RUNNING_LOCK

**参数：**

| 参数名 | 类型                                | 必填 | 说明               |
| ------ | ----------------------------------- | ---- | ------------------ |
| name   | string                              | 是   | 锁的名字。建议使用包名或类名加后缀的方式命名。|
| type   | [RunningLockType](#runninglocktype) | 是   | 要创建的锁的类型。 |

**返回值：**

| 类型                                       | 说明                                 |
| ------------------------------------------ | ------------------------------------ |
| Promise&lt;[RunningLock](#runninglock)&gt; | Promise对象，返回RunningLock锁对象。 |

**示例：**

```js
runningLock.createRunningLock('running_lock_test', runningLock.RunningLockType.BACKGROUND)
.then((lock: runningLock.RunningLock) => {
    console.info('created running lock: ' + lock);
})
.catch((err: BusinessError) => {
    console.error(`Failed to create running lock. Code: ${err.code}, message: ${err.message}`);
});
```

## RunningLock

阻止系统睡眠或使能接近光控制亮灭屏的锁，不同的锁类型具有不同的功能，详见[RunningLockType](#runninglocktype)。

需结合[create](#runninglockcreate9)创建锁、[hold](#hold9)持锁、[unhold](#unhold9)释放锁使用。具体使用方法见示例。

### hold<sup>9+</sup>

hold(timeout: number): void

锁定和持有RunningLock。适用于应用需要在后台持续运行（如后台下载、长时间定位追踪等）时阻止系统睡眠的场景或通话时需要接近光控制亮灭屏的场景等。调用此方法后，必须在使用完毕时调用unhold()释放锁，或者在调用时设置超时释放时间由系统自动释放，与unhold()方法配对使用。未释放锁会导致阻止睡眠或者控制亮灭屏功能持续生效。

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**需要权限：** ohos.permission.RUNNING_LOCK

**参数：**

| 参数名  | 类型   | 必填 | 说明                                      |
| ------- | ------ | ---- | ----------------------------------------- |
| timeout | number | 是   | 锁定和持有RunningLock的时长，单位：毫秒。<br>**-1**：永久持锁，需要主动释放。<br>**0**：默认3s后超时释放。<br>**>0**：按传入值超时释放。|

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID   | 错误信息     |
|---------|----------|
| 401     | Parameter error. Possible causes: 1. Incorrect parameter types; 2. Parameter verification failed. |
| 201     | If the permission is denied.|

**示例：**

```ts
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

### unhold<sup>9+</sup>

unhold(): void

释放RunningLock锁。此方法与hold()配对使用，在调用hold()锁定后调用此方法释放锁。

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**需要权限：** ohos.permission.RUNNING_LOCK

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID   | 错误信息     |
|---------|----------|
| 201     | If the permission is denied.|


**示例：**

```ts
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

### isHolding<sup>9+</sup>

isHolding(): boolean

查询当前RunningLock是持有状态还是释放状态。

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**返回值：**

| 类型    | 说明                                                         |
| ------- | ------------------------------------------------------------ |
| boolean | 返回true表示当前RunningLock是持有状态，返回false表示当前RunningLock是释放状态。 |

**示例：**

```ts
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

### lock<sup>(deprecated)</sup>

lock(timeout: number): void

持有RunningLock锁。

> **说明：**<br>从 API version 7开始支持，从 API version 9开始废弃。建议使用[RunningLock.hold](#hold9)替代。

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**需要权限：** ohos.permission.RUNNING_LOCK

**参数：**

| 参数名  | 类型   | 必填 | 说明                                      |
| ------- | ------ | ---- | ----------------------------------------- |
| timeout | number | 是   | 锁定和持有RunningLock的时长，单位：毫秒。 |

**示例：**

```js
runningLock.createRunningLock('running_lock_test', runningLock.RunningLockType.BACKGROUND)
.then((lock: runningLock.RunningLock) => {
    lock.lock(500);
    console.info('create running lock and lock success');
})
.catch((err: BusinessError) => {
    console.error(`Failed to create running lock. Code: ${err.code}, message: ${err.message}`);
});
```

### unlock<sup>(deprecated)</sup>

unlock(): void

释放RunningLock锁。

> **说明：**<br>从 API version 7开始支持，从 API version 9开始废弃。建议使用[RunningLock.unhold](#unhold9)替代。

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**需要权限：** ohos.permission.RUNNING_LOCK

**示例：**

```js
runningLock.createRunningLock('running_lock_test', runningLock.RunningLockType.BACKGROUND)
.then((lock: runningLock.RunningLock) => {
    lock.unlock();
    console.info('create running lock and unlock success');
})
.catch((err: BusinessError) => {
    console.error(`Failed to create running lock. Code: ${err.code}, message: ${err.message}`);
});
```

### isUsed<sup>(deprecated)</sup>

isUsed(): boolean

查询当前RunningLock是持有状态还是释放状态。

> **说明：**<br>从 API version 7开始支持，从 API version 9开始废弃。建议使用[RunningLock.isHolding](#isholding9)替代。

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**返回值：**
| 类型    | 说明                                                         |
| ------- | ------------------------------------------------------------ |
| boolean | 返回true表示当前RunningLock是持有状态，返回false表示当前RunningLock是释放状态。 |

**示例：**

```js
runningLock.createRunningLock('running_lock_test', runningLock.RunningLockType.BACKGROUND)
.then((lock: runningLock.RunningLock) => {
    let isUsed = lock.isUsed();
    console.info('check running lock used status: ' + isUsed);
})
.catch((err: BusinessError) => {
    console.error(`Failed to check running lock used status. Code: ${err.code}, message: ${err.message}`);
});
```

## RunningLockType

RunningLock锁的类型。

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

| 名称                              | 值   | 说明                                                         |
| --------------------------------- | ---- | ------------------------------------------------------------ |
| BACKGROUND<sup>(deprecated)</sup> | 1    | 阻止系统睡眠的锁。<br>**说明：** 从 API version 7开始支持，从 API version 10开始废弃。 |
| PROXIMITY_SCREEN_CONTROL          | 2    | 接近光锁，使能接近光传感器，并根据传感器与障碍物的距离远近发起亮灭屏流程。  |
| BACKGROUND_USER_IDLE<sup>23+</sup>| 129  | 阻止系统自动睡眠的后台闲时任务锁，持锁能保证一段时间用户不活动后系统不进入自动睡眠。<br>**注意：** 不能阻止如PC合盖等场景系统进入强制睡眠，使用方必须监听[COMMON_EVENT_ENTER_FORCE_SLEEP](./common_event/commonEventManager-definitions.md#common_event_enter_force_sleep12)，监听到事件后释放该锁。该类型锁行为存在设备差异，使用该类型锁请参考[阻止系统闲时进入睡眠开发指南](../../basic-services/powermgr/runningLock/runningLock-dev.md)。|
