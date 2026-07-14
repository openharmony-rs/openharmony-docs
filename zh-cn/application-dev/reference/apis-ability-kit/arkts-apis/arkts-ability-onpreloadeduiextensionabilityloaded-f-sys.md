# onPreloadedUIExtensionAbilityLoaded（系统接口）

## onPreloadedUIExtensionAbilityLoaded

```TypeScript
function onPreloadedUIExtensionAbilityLoaded(callback: PreloadedUIExtensionAbilityLoadedFn): void
```

监听当前进程中预加载的[UIExtensionAbility](arkts-ability-uiextensionability-c.md)实例的加载事件。

**起始版本：** 23

**需要权限：** ohos.permission.PRELOAD_UI_EXTENSION_ABILITY

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | PreloadedUIExtensionAbilityLoadedFn | 是 | 用于接收被加载的预加载[UIExtensionAbility](arkts-ability-uiextensionability-c.md)实例ID的回调函数。 |

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

function onPreloadLoaded(preloadId: number) {
  console.info(`Preloaded UIExtensionAbility loaded, preloadId: ${preloadId}`);
}

try {
  abilityManager.onPreloadedUIExtensionAbilityLoaded(onPreloadLoaded);
  console.info('onPreloadedUIExtensionAbilityLoaded success.');
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error(`onPreloadedUIExtensionAbilityLoaded failed, code is ${code}, message is ${message}`);
}

```

