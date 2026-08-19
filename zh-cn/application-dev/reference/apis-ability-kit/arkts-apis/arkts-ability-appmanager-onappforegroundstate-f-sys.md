# on_appForegroundState（系统接口）

## 导入模块

```TypeScript
import { appManager } from '@kit.AbilityKit';
```

## on('appForegroundState')

```TypeScript
function on(type: 'appForegroundState', observer: AppForegroundStateObserver): void
```

注册应用启动和退出的监听器，可用于系统应用监听所有应用的启动和退出。

**起始版本：** 11

**需要权限：** ohos.permission.RUNNING_STATE_OBSERVER

<!--Device-appManager-function on(type: 'appForegroundState', observer: AppForegroundStateObserver): void--><!--Device-appManager-function on(type: 'appForegroundState', observer: AppForegroundStateObserver): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'appForegroundState' | 是 | 调用接口类型，固定填'appForegroundState'字符串。 |
| observer | AppForegroundStateObserver | 是 | 应用状态监听器，用于监听应用的启动和退出。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |

**示例**

```TypeScript
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let observer: appManager.AppForegroundStateObserver = {
  onAppStateChanged(appStateData) {
    console.info(`[appManager] onAppStateChanged: ${JSON.stringify(appStateData)}`);
  },
};

try {
  appManager.on('appForegroundState', observer);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```

