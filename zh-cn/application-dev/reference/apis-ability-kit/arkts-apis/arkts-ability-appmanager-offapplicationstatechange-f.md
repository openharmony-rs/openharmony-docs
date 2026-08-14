# offApplicationStateChange

## offApplicationStateChange

```TypeScript
function offApplicationStateChange(observerId: int, callback: AsyncCallback<void>): void
```

注销应用状态监听器。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.RUNNING_STATE_OBSERVER

<!--Device-appManager-function offApplicationStateChange(observerId: int, callback: AsyncCallback<void>): void--><!--Device-appManager-function offApplicationStateChange(observerId: int, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| observerId | int | 是 | 注册的应用状态监听器ID。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | The callback of off. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

## 示例

ArkTS-Sta示例：

```TypeScript
'use static'
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let observerId = 0;

// 1.注册应用状态监听器
class CustomApplicationStateObserver implements appManager.ApplicationStateObserver {
  public appStateData?: appManager.AppStateData;
  public abilityStateData?: appManager.AbilityStateData;
  public processData?: appManager.ProcessData;

  onForegroundApplicationChanged(appStateData: appManager.AppStateData): void {
    console.info(`[appManager] onForegroundApplicationChanged: ${JSON.stringify(appStateData)}`);
  }

  onAbilityStateChanged(abilityStateData: appManager.AbilityStateData): void {
    console.info(`[appManager] onAbilityStateChanged: ${JSON.stringify(abilityStateData)}`);
  }

  onProcessCreated(processData: appManager.ProcessData): void {
    console.info(`[appManager] onProcessCreated: ${JSON.stringify(processData)}`);
  }

  onProcessDied(processData: appManager.ProcessData): void {
    console.info(`[appManager] onProcessDied: ${JSON.stringify(processData)}`);
  }

  onProcessStateChanged(processData: appManager.ProcessData) {
    console.info(`[appManager] onProcessStateChanged: ${JSON.stringify(processData)}`);
  }

  onAppStarted(appStateData: appManager.AppStateData) {
    console.info(`[appManager] onAppStarted: ${JSON.stringify(appStateData)}`);
  }

  onAppStopped(appStateData: appManager.AppStateData) {
    console.info(`[appManager] onAppStopped: ${JSON.stringify(appStateData)}`);
  }
}

let bundleNameList = ['bundleName1', 'bundleName2'];

try {
  let applicationStateObserver = new CustomApplicationStateObserver();
  observerId = appManager.onApplicationStateChange(applicationStateObserver, bundleNameList);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}

function offCallback(err: BusinessError<void> | null) {
  if (err) {
    console.error(`appmanager.off failed, code: ${err.code}, msg: ${err.message}`);
  } else {
    console.info(`appmanager.off success.`);
  }
}

// 2.注销应用状态监听器
try {
  appManager.offApplicationStateChange(observerId, offCallback);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```


## offApplicationStateChange

```TypeScript
function offApplicationStateChange(observerId: int): Promise<void>
```

注销应用状态监听器。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.RUNNING_STATE_OBSERVER

<!--Device-appManager-function offApplicationStateChange(observerId: int): Promise<void>--><!--Device-appManager-function offApplicationStateChange(observerId: int): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| observerId | int | 是 | 注册的应用状态监听器ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | The promise returned by the function. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

## 示例

ArkTS-Sta示例：

```TypeScript
'use static'
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let observerId = 0;

// 1.注册应用状态监听器
class CustomApplicationStateObserver implements appManager.ApplicationStateObserver {
  public appStateData?: appManager.AppStateData;
  public abilityStateData?: appManager.AbilityStateData;
  public processData?: appManager.ProcessData;

  onForegroundApplicationChanged(appStateData: appManager.AppStateData): void {
    console.info(`[appManager] onForegroundApplicationChanged: ${JSON.stringify(appStateData)}`);
  }

  onAbilityStateChanged(abilityStateData: appManager.AbilityStateData): void {
    console.info(`[appManager] onAbilityStateChanged: ${JSON.stringify(abilityStateData)}`);
  }

  onProcessCreated(processData: appManager.ProcessData): void {
    console.info(`[appManager] onProcessCreated: ${JSON.stringify(processData)}`);
  }

  onProcessDied(processData: appManager.ProcessData): void {
    console.info(`[appManager] onProcessDied: ${JSON.stringify(processData)}`);
  }

  onProcessStateChanged(processData: appManager.ProcessData) {
    console.info(`[appManager] onProcessStateChanged: ${JSON.stringify(processData)}`);
  }

  onAppStarted(appStateData: appManager.AppStateData) {
    console.info(`[appManager] onAppStarted: ${JSON.stringify(appStateData)}`);
  }

  onAppStopped(appStateData: appManager.AppStateData) {
    console.info(`[appManager] onAppStopped: ${JSON.stringify(appStateData)}`);
  }
}

let bundleNameList = ['bundleName1', 'bundleName2'];

try {
  let applicationStateObserver = new CustomApplicationStateObserver();
  observerId = appManager.onApplicationStateChange(applicationStateObserver, bundleNameList);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}

// 2.注销应用状态监听器
try {
  appManager.offApplicationStateChange(observerId).then(() => {
    console.info(`unregisterApplicationStateObserver success`);
  }).catch((err: Error) => {
    console.error(`unregisterApplicationStateObserver fail, err: ${err.message}`);
  });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```

