# onPreloadedUIExtensionAbilityDestroyed（系统接口）

## 导入模块

```TypeScript
import { abilityManager } from '@kit.AbilityKit';
```

## onPreloadedUIExtensionAbilityDestroyed

```TypeScript
function onPreloadedUIExtensionAbilityDestroyed(callback: PreloadedUIExtensionAbilityDestroyedFn): void
```

监听当前进程中预加载的[UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md)实例的销毁事件。

**起始版本：** 23

**需要权限：** ohos.permission.PRELOAD_UI_EXTENSION_ABILITY

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-abilityManager-function onPreloadedUIExtensionAbilityDestroyed(callback: PreloadedUIExtensionAbilityDestroyedFn): void--><!--Device-abilityManager-function onPreloadedUIExtensionAbilityDestroyed(callback: PreloadedUIExtensionAbilityDestroyedFn): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [PreloadedUIExtensionAbilityDestroyedFn](arkts-ability-abilitymanager-preloadeduiextensionabilitydestroyedfn-t-sys.md) | 是 | 用于接收被销毁的预加载[UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md)实例ID的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not system-app, can not use system-api. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. Possible causes: Memory operation error. |

**示例：**

```TypeScript
import { abilityManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

function onPreloadDestroyed(preloadId: number) {
  console.info(`Preloaded UIExtensionAbility destroyed, preloadId: ${preloadId}`);
}

try {
  abilityManager.onPreloadedUIExtensionAbilityDestroyed(onPreloadDestroyed);
  console.info('onPreloadedUIExtensionAbilityDestroyed success.');
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error(`onPreloadedUIExtensionAbilityDestroyed failed, code is ${code}, message is ${message}`);
}

```

