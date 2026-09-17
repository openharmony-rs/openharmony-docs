# setAlternateIcon

## Modules to Import

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## setAlternateIcon

```TypeScript
function setAlternateIcon(alternateIconName: string): Promise<void>
```

Sets the alternate icon of the caller based on the given alternate icon name. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| alternateIconName | string | Yes | Name of the alternate icon to be set. The alternate icon name must be in the name field of alternateIcons in app.json5. If alternateIconName is left empty, the alternate icon is canceled. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17700308](../errorcode-bundle.md#17700308-alternate-icon-name-not-configured-in-the-configuration-file) | The alternateIconName must match the name field under alternateIcons in the app.json5 file. |
| [17700309](../errorcode-bundle.md#17700309-no-alternate-icon-is-enabled) | No alternate icon is enabled. |
| [17700310](../errorcode-bundle.md#17700310-failed-to-set-the-alternate-icon) | Failed to set the alternate icon. |

**Examples**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

// Replace alternateIconName with the name of the alternate icon to set.
let alternateIconName: string = 'com.ohos.demo';

try {
  bundleManager.setAlternateIcon(alternateIconName).then((data) => {
    hilog.info(0x0000, 'testTag', 'setAlternateIcon successfully');
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'setAlternateIcon failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'setAlternateIcon failed. Cause: %{public}s', message);
}
```
