# offAppForegroundStateChange（系统接口）

## 导入模块

```TypeScript
import { appManager } from '@kit.AbilityKit';
```

## offAppForegroundStateChange

```TypeScript
function offAppForegroundStateChange(observer?: AppForegroundStateObserver): void
```

注销应用启动和退出的监听器。

**起始版本：** 23

**需要权限：** ohos.permission.RUNNING_STATE_OBSERVER

<!--Device-appManager-function offAppForegroundStateChange(observer?: AppForegroundStateObserver): void--><!--Device-appManager-function offAppForegroundStateChange(observer?: AppForegroundStateObserver): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| observer | AppForegroundStateObserver | 否 | 取消注册的应用启动和退出监听器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |

**示例**

ArkTS-Sta示例：

```TypeScript
'use static'
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class AppForegroundStateObserverCustom implements appManager.AppForegroundStateObserver {
  onAppStateChanged(appStateData: appManager.AppStateData) {
    console.info(`[appManager] onAppStateChanged: ${JSON.stringify(appStateData)}`);
  }
}

let observer_: appManager.AppForegroundStateObserver | undefined;
try {
  let observer = new AppForegroundStateObserverCustom();
  appManager.onAppForegroundStateChange(observer);
  // 保存observer对象，用于注销
  observer_ = observer;
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}

// 2.注销监听器
try {
  appManager.offAppForegroundStateChange(observer_);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```

