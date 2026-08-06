# onAbilityForegroundState（系统接口）

## onAbilityForegroundState

```TypeScript
function onAbilityForegroundState(observer: AbilityForegroundStateObserver): void
```

注册Ability的启动和退出的观测器。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**需要权限：** ohos.permission.RUNNING_STATE_OBSERVER

<!--Device-abilityManager-function onAbilityForegroundState(observer: AbilityForegroundStateObserver): void--><!--Device-abilityManager-function onAbilityForegroundState(observer: AbilityForegroundStateObserver): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| observer | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Ability状态观测器，用于观测Ability的启动和退出。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Connect to system server failed. |

**示例：**

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

try {
  let observer = new AbilityForegroundStateObserverCustom();
  abilityManager.onAbilityForegroundState(observer);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`error: ${code}, ${message} `);
}
```

