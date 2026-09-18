# getAbilityInfo

## Modules to Import

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## getAbilityInfo

```TypeScript
function getAbilityInfo(uri: string, abilityFlags: number): Promise<Array<AbilityInfo>>
```

Obtains the ability information based on the given resource identifier and ability flag. This API uses a promise to return the result.

**Since:** 20

**Required permissions:** ohos.permission.GET_ABILITY_INFO

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | URI of the resource. The value is the same as that of the [uris field under skills in the module.json5 file](../../../quick-start/module-configuration-file.md#skills). |
| abilityFlags | number | Yes | [Ability flag](arkts-ability-bundlemanager-abilityflag-e.md), indicating the ability information to be obtained. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[AbilityInfo](arkts-ability-bundlemanager-abilityinfo-t.md)&gt;&gt; | Promise used to return an array of ability information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [17700003](../errorcode-bundle.md#17700003-ability-name-does-not-exist) | The ability is not found. |

**Examples**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let abilityFlags = bundleManager.AbilityFlag.GET_ABILITY_INFO_WITH_APPLICATION;
let uri = "https://www.example.com";

try {
  bundleManager.getAbilityInfo(uri, abilityFlags).then((data) => {
    hilog.info(0x0000, 'testTag', 'getAbilityInfo successfully. Data: %{public}s', JSON.stringify(data));
  }).catch((err: BusinessError) => {
    let message = (err as BusinessError).message;
    hilog.error(0x0000, 'testTag', 'getAbilityInfo failed. Cause: %{public}s', message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAbilityInfo failed. Cause: %{public}s', message);
}
```
