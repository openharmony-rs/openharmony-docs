# offAbilityForegroundState（系统接口）

## 导入模块

```TypeScript
import { abilityManager } from '@kit.AbilityKit';
```

## offAbilityForegroundState

```TypeScript
function offAbilityForegroundState(observer?: AbilityForegroundStateObserver): void
```

取消注册Ability启动和退出的观测器。

**起始版本：** 23

**需要权限：** ohos.permission.RUNNING_STATE_OBSERVER

<!--Device-abilityManager-function offAbilityForegroundState(observer?: AbilityForegroundStateObserver): void--><!--Device-abilityManager-function offAbilityForegroundState(observer?: AbilityForegroundStateObserver): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| observer | AbilityForegroundStateObserver | 否 | Ability状态观测器，用于观测Ability的启动和退出。如果未配置该参数，则取消当前应用注册的所有observer。如果配置 了该参数，则取消该observer。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Connect to system server failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |

**示例**

ArkTS-Sta示例：

```TypeScript
'use static'
import { abilityManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class AbilityForegroundStateObserverCustom implements abilityManager.AbilityForegroundStateObserver {
  onAbilityStateChanged(abilityStateData: abilityManager.AbilityStateData) {
    console.info(`onAbilityStateChanged: ${JSON.stringify(abilityStateData)}`);
  }
}

let observer_: abilityManager.AbilityForegroundStateObserver | undefined;
// 1.注册应用启动和退出的监听器
try {
  let observer = new AbilityForegroundStateObserverCustom();
  abilityManager.onAbilityForegroundState(observer);
  observer_ = observer;
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`error: ${code}, ${message} `);
}

// 2.注销监听器
try {
  abilityManager.offAbilityForegroundState(observer_);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`error: ${code}, ${message} `);
}
```

