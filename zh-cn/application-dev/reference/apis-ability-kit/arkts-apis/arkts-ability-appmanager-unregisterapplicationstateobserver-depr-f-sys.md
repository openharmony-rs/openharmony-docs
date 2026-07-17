# unregisterApplicationStateObserver（系统接口）

## unregisterApplicationStateObserver

```TypeScript
function unregisterApplicationStateObserver(observerId: number, callback: AsyncCallback<void>): void
```

取消注册应用程序状态观测器。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** off

**需要权限：** ohos.permission.RUNNING_STATE_OBSERVER

<!--Device-appManager-function unregisterApplicationStateObserver(observerId: number, callback: AsyncCallback<void>): void--><!--Device-appManager-function unregisterApplicationStateObserver(observerId: number, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| observerId | number | 是 | 表示观察者的编号代码。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 表示指定的callback回调方法。 |

**示例：**

```TypeScript
import appManager from '@ohos.application.appManager';
import { BusinessError } from '@ohos.base';

let observerId = 100;

function unregisterApplicationStateObserverCallback(err: BusinessError) {
  if (err) {
    console.error(`UnregisterApplicationStateObserverCallback failed, error code: ${err.code}, error msg: ${err.message}.`);
    return;
  }
}

appManager.unregisterApplicationStateObserver(observerId, unregisterApplicationStateObserverCallback);

```


## unregisterApplicationStateObserver

```TypeScript
function unregisterApplicationStateObserver(observerId: number): Promise<void>
```

取消注册应用程序状态观测器。使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** off

**需要权限：** ohos.permission.RUNNING_STATE_OBSERVER

<!--Device-appManager-function unregisterApplicationStateObserver(observerId: number): Promise<void>--><!--Device-appManager-function unregisterApplicationStateObserver(observerId: number): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| observerId | number | 是 | 表示观察者的编号代码。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象。无返回结果的Promise对象。 |

**示例：**

```TypeScript
import appManager from '@ohos.application.appManager';
import { BusinessError } from '@ohos.base';

let observerId = 100;

appManager.unregisterApplicationStateObserver(observerId)
.then((data) => {
    console.info(`unregisterApplicationStateObserver success, data: ${data}.`);
})
.catch((err: BusinessError) => {
    console.error(`unregisterApplicationStateObserver failed, err code: ${err.code}, err msg: ${err.message}.`);
});

```

