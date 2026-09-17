# getLaunchWant

## Modules to Import

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## getLaunchWant

```TypeScript
function getLaunchWant(): Want
```

Obtains the **Want** parameters of the [entry UIAbility](../../../application-models/ability-terminology.md#uiability) of the current application.

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**Return value:**

| Type | Description |
| --- | --- |
| [Want](arkts-ability-app-ability-want-want-c.md) | Want object that contains only the bundle name and ability name. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17700072](../errorcode-bundle.md#17700072-launch-want-does-not-exist) | The launch want is not found. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { bundleManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let want = bundleManager.getLaunchWant();
  hilog.info(0x0000, 'testTag', 'getLaunchWant ability name: %{public}s', want.abilityName);
  hilog.info(0x0000, 'testTag', 'getLaunchWant bundle name: %{public}s', want.bundleName);
} catch (error) {
  let message = (error as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getLaunchWant failed: %{public}s', message);
}
```
