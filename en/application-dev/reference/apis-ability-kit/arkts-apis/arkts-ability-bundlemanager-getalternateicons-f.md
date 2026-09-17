# getAlternateIcons

## Modules to Import

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## getAlternateIcons

```TypeScript
function getAlternateIcons(): Promise<Array<AlternateIconInfo>>
```

Queries the alternate icon information configured in the alternateIcons in the app.json5 of the current application. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[AlternateIconInfo](arkts-ability-bundlemanager-alternateiconinfo-t.md)&gt;&gt; | Promise used to return the list of alternate icons of the current application. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17700311](../errorcode-bundle.md#17700311-failed-to-obtain-the-alternate-icon) | Failed to obtain the alternate icon. |

**Examples**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  bundleManager.getAlternateIcons().then((data) => {
    hilog.info(0x0000, 'testTag', 'getAlternateIcons successfully. Data: %{public}s', JSON.stringify(data));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getAlternateIcons failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAlternateIcons failed. Cause: %{public}s', message);
}
```
