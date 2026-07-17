# isRunningLockTypeSupported

## 导入模块

```TypeScript
import { runningLock } from '@kit.BasicServicesKit';
```

## isRunningLockTypeSupported

```TypeScript
function isRunningLockTypeSupported(type: RunningLockType, callback: AsyncCallback<boolean>): void
```

查询系统是否支持该类型的锁。使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [isSupported](arkts-basicservices-runninglock-issupported-f.md#issupported-1)

<!--Device-runningLock-function isRunningLockTypeSupported(type: RunningLockType, callback: AsyncCallback<boolean>): void--><!--Device-runningLock-function isRunningLockTypeSupported(type: RunningLockType, callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [RunningLockType](arkts-basicservices-runninglock-runninglocktype-e.md) | 是 | 需要查询的锁的类型。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)<boolean> | 是 | 回调函数。当查询成功，err为undefined，data为获取到的支持情况，返回true表示支持，返回false表示不支持；否则为错误对象。 |

**示例：**

```TypeScript
runningLock.isRunningLockTypeSupported(runningLock.RunningLockType.BACKGROUND, (err: BusinessError, data: boolean) => {
    if (err) {
        console.error(`Failed to check BACKGROUND lock support status. Code: ${err.code}, message: ${err.message}`);
    } else {
        console.info('BACKGROUND lock support status: ' + data);
    }
});

```


## isRunningLockTypeSupported

```TypeScript
function isRunningLockTypeSupported(type: RunningLockType): Promise<boolean>
```

查询系统是否支持该类型的锁。使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [isSupported](arkts-basicservices-runninglock-issupported-f.md#issupported-1)

<!--Device-runningLock-function isRunningLockTypeSupported(type: RunningLockType): Promise<boolean>--><!--Device-runningLock-function isRunningLockTypeSupported(type: RunningLockType): Promise<boolean>-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [RunningLockType](arkts-basicservices-runninglock-runninglocktype-e.md) | 是 | 需要查询的锁的类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<boolean> | Promise对象。返回true表示支持；返回false表示不支持。 |

**示例：**

```TypeScript
runningLock.isRunningLockTypeSupported(runningLock.RunningLockType.BACKGROUND)
.then((data: boolean) => {
    console.info('BACKGROUND lock support status: ' + data);
})
.catch((err: BusinessError) => {
    console.error(`Failed to check BACKGROUND lock support status. Code: ${err.code}, message: ${err.message}`);
});

```

