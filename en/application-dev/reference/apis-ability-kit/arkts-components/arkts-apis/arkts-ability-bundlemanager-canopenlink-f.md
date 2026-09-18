# canOpenLink

## Modules to Import

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## canOpenLink

```TypeScript
function canOpenLink(link: string): boolean
```

Checks whether the target application can be accessed based on the provided link. The scheme specified in the link must be configured in the **querySchemes** field of the [module.json5](../../../quick-start/module-configuration-file.md) file.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| link | string | Yes | Link to check. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for whether the link can be opened. **true** if it can be opened, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700055](../errorcode-bundle.md#17700055-invalid-link) | The specified link is invalid. |
| [17700056](../errorcode-bundle.md#17700056-scheme-of-the-link-not-configured-in-queryschemes) | The scheme of the specified link is not in the querySchemes. |

**Examples**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let link = 'welink://';
  let data = bundleManager.canOpenLink(link);
  hilog.info(0x0000, 'testTag', 'canOpenLink successfully: %{public}s', JSON.stringify(data));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'canOpenLink failed: %{public}s', message);
}
```
