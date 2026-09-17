# getProfileByExtensionAbilitySync

## Modules to Import

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## getProfileByExtensionAbilitySync

```TypeScript
function getProfileByExtensionAbilitySync(moduleName: string, extensionAbilityName: string, metadataName?: string): Array<string>
```

Obtains the JSON string array of the current application's configuration file based on the given module name, ExtensionAbility name, and metadata name (name configured in [metadata](../../../quick-start/module-configuration-file.md#metadata) of the **module.json5** file). This API returns the result synchronously. The result value is a string array.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| moduleName | string | Yes | Module name. |
| extensionAbilityName | string | Yes | Name of the ExtensionAbility component. |
| metadataName | string | No | Metadata name of the ExtensionAbility component, that is, **name** of the **metadata** tag under [extensionAbilities](../../../quick-start/module-configuration-file.md#extensionabilities) in the **module.json5** file. The default value is null. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | An array of JSON strings. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700002](../errorcode-bundle.md#17700002-module-name-does-not-exist) | The specified moduleName is not existed. |
| [17700003](../errorcode-bundle.md#17700003-ability-name-does-not-exist) | The specified extensionAbilityName not existed. |
| [17700024](../errorcode-bundle.md#17700024-profile-does-not-exist) | Failed to get the profile because there is no profile in the HAP. |

**Examples**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let moduleName = 'entry';
let extensionAbilityName = 'com.example.myapplication.extension';
let metadataName = 'ability_metadata';

try {
  let data = bundleManager.getProfileByExtensionAbilitySync(moduleName, extensionAbilityName);
  hilog.info(0x0000, 'testTag', 'getProfileByExtensionAbilitySync successfully. Data: %{public}s',
    JSON.stringify(data));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getProfileByExtensionAbilitySync failed. Cause: %{public}s', message);
}

try {
  let data = bundleManager.getProfileByExtensionAbilitySync(moduleName, extensionAbilityName, metadataName);
  hilog.info(0x0000, 'testTag', 'getProfileByExtensionAbilitySync successfully. Data: %{public}s',
    JSON.stringify(data));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getProfileByExtensionAbilitySync failed. Cause: %{public}s', message);
}
```
