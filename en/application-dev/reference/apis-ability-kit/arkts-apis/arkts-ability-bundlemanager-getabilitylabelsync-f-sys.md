# getAbilityLabelSync (System API)

## Modules to Import

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## getAbilityLabelSync

```TypeScript
function getAbilityLabelSync(bundleName: string, moduleName: string, abilityName: string): string
```

Obtains the ability label based on the given bundle name, module name, and ability name. This API returns the result synchronously.

No permission is required for obtaining the caller's own information.

**Since:** 10

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**System capability:** SystemCapability.BundleManager.BundleFramework.Resource

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name. |
| moduleName | string | Yes | Module name. |
| abilityName | string | Yes | Name of the UIAbility component. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Label of the ability. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundleName is not found. |
| [17700002](../errorcode-bundle.md#17700002-module-name-does-not-exist) | The specified moduleName is not found. |
| [17700003](../errorcode-bundle.md#17700003-ability-name-does-not-exist) | The specified abilityName is not found. |
| [17700026](../errorcode-bundle.md#17700026-bundle-disabled) | The specified bundle is disabled. |
| [17700029](../errorcode-bundle.md#17700029-disabled-ability) | The specified ability is disabled. |

**Examples**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = 'com.example.myapplication';
let moduleName = 'entry';
let abilityName = 'EntryAbility';

try {
  let abilityLabel = bundleManager.getAbilityLabelSync(bundleName, moduleName, abilityName);
  hilog.info(0x0000, 'testTag', 'getAbilityLabelSync successfully. Data: %{public}s', abilityLabel);
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAbilityLabelSync failed. Cause: %{public}s', message);
}
```
