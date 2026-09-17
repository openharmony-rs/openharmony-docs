# offPreloadedUIExtensionAbilityLoaded (System API)

## Modules to Import

```TypeScript
import { abilityManager } from '@kit.AbilityKit';
```

## offPreloadedUIExtensionAbilityLoaded

```TypeScript
function offPreloadedUIExtensionAbilityLoaded(callback?: PreloadedUIExtensionAbilityLoadedFn): void
```

Unsubscribes from loaded events of a preloaded [UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md) instance in the current process.

**Since:** 23

**Required permissions:** ohos.permission.PRELOAD_UI_EXTENSION_ABILITY

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [PreloadedUIExtensionAbilityLoadedFn](arkts-ability-abilitymanager-preloadeduiextensionabilityloadedfn-t-sys.md) | No | Callback used for unsubscription. If this parameter is not specified, all callbacks associated with the specified event in the process will be unregistered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not system-app, can not use system-api. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. Possible causes: Memory operation error. |

**Examples**

```TypeScript
import { abilityManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

function offPreloadLoaded(preloadId: number) {
  console.info(`Preloaded UIExtensionAbility loaded, preloadId: ${preloadId}`);
}

try {
  abilityManager.offPreloadedUIExtensionAbilityLoaded(offPreloadLoaded);
  console.info('offPreloadedUIExtensionAbilityLoaded success.');
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error(`offPreloadedUIExtensionAbilityLoaded failed, code is ${code}, message is ${message}`);
}
```
