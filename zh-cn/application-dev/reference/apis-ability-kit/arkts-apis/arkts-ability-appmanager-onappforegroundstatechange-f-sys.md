# onAppForegroundStateChange（系统接口）

## onAppForegroundStateChange

```TypeScript
function onAppForegroundStateChange(observer: AppForegroundStateObserver): void
```

注册应用启动和退出的监听器，可用于系统应用监听所有应用的启动和退出。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.RUNNING_STATE_OBSERVER

<!--Device-appManager-function onAppForegroundStateChange(observer: AppForegroundStateObserver): void--><!--Device-appManager-function onAppForegroundStateChange(observer: AppForegroundStateObserver): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| observer | AppForegroundStateObserver | 是 | 应用状态监听器，用于监听应用的启动和退出。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |

## 示例

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

try {
  let observer = new AppForegroundStateObserverCustom();
  appManager.onAppForegroundStateChange(observer);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```

