# getSelfManagedBrowserPolicyVersion

## Modules to Import

```TypeScript
import { browser } from '@kit.MDMKit';
```

## getSelfManagedBrowserPolicyVersion

```TypeScript
function getSelfManagedBrowserPolicyVersion(): string
```

Obtains the browser policy version of the current device.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Return value:**

| Type | Description |
| --- | --- |
| string | Browser policy version. |

**Examples**

```TypeScript
import { browser } from '@kit.MDMKit';

try {
  let version: string = browser.getSelfManagedBrowserPolicyVersion();
  console.info(`Succeeded in getting self managed browser policy version, result : ${version}`);
} catch(err) {
  console.error(`Failed to get self managed browser policy version. Code is ${err.code}, message is ${err.message}`);
}
```
