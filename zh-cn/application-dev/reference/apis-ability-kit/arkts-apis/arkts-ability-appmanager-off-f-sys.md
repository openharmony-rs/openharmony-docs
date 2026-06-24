# off（系统接口）

## off('appForegroundState')

```TypeScript
function off(type: 'appForegroundState', observer?: AppForegroundStateObserver): void
```

注销应用启动和退出的监听器。

**起始版本：** 11

**需要权限：** ohos.permission.RUNNING_STATE_OBSERVER

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'appForegroundState' | 是 | 调用接口类型，固定填'appForegroundState'字符串。 |
| observer | AppForegroundStateObserver | 否 | 取消注册的应用启动和退出监听器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Not) | Not system application. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |

**示例：**

```TypeScript
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let observer_: appManager.AppForegroundStateObserver | undefined;
// 1.注册应用启动和退出的监听器
let observer: appManager.AppForegroundStateObserver = {
  onAppStateChanged(appStateData: appManager.AppStateData) {
    console.info(`[appManager] onAppStateChanged: ${JSON.stringify(appStateData)}`);
  },
};

try {
  appManager.on('appForegroundState', observer);
  // 保存observer对象，用于注销
  observer_ = observer;
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}

// 2.注销监听器
try {
  appManager.off('appForegroundState',  observer_);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}

```


## off('abilityFirstFrameState')

```TypeScript
function off(type: 'abilityFirstFrameState', observer?: AbilityFirstFrameStateObserver): void
```

取消注册监听Ability首帧绘制完成事件观察者对象。

**起始版本：** 12

**需要权限：** ohos.permission.RUNNING_STATE_OBSERVER

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'abilityFirstFrameState' | 是 | 调用接口类型，固定填'abilityFirstFrameState'字符串。 |
| observer | AbilityFirstFrameStateObserver | 否 | 表示待取消的Ability首帧绘制完成事件观察者对象，不填表示取消所有监听对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Not) | Not system application. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |

**示例：**

```TypeScript
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let abilityFirstFrameStateObserverForAll: appManager.AbilityFirstFrameStateObserver = {
  onAbilityFirstFrameDrawn(abilityStateData: appManager.AbilityFirstFrameStateData) {
    console.info("abilityFirstFrame: ", JSON.stringify(abilityStateData));
  }
};

try {
  appManager.on('abilityFirstFrameState', abilityFirstFrameStateObserverForAll);
} catch (e) {
  let code = (e as BusinessError).code;
  let message = (e as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}

try {
  appManager.off('abilityFirstFrameState', abilityFirstFrameStateObserverForAll);
} catch (e) {
  let code = (e as BusinessError).code;
  let message = (e as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}

```

