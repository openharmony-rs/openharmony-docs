# setShortcutVisibleForSelf

## Modules to Import

```TypeScript
import { shortcutManager } from '@kit.AbilityKit';
```

## setShortcutVisibleForSelf

```TypeScript
function setShortcutVisibleForSelf(id: string, visible: boolean): Promise<void>
```

Sets whether to display the specified shortcut for the current application. This API uses a promise to return the result.

**Since:** 20

**System capability:** SystemCapability.BundleManager.BundleFramework.Launcher

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string | Yes | Shortcut ID, which is the value of the **shortcutId** field under the **shortcuts** tag in the [module.json5](../../../quick-start/module-configuration-file.md) file. The value is a string of up to 63 bytes. |
| visible | boolean | Yes | Whether to display the shortcut. **true** to display, **false** otherwise. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17700070](../errorcode-bundle.md#17700070-invalid-shortcut-id) | The specified shortcut id is not exist. |

**Examples**

```TypeScript
import { shortcutManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Replace it with the shortcutId field under the shortcuts tag of the module.json5 file.
shortcutManager.setShortcutVisibleForSelf("shortcut_id", false)
  .then(() => {
    console.info('setShortcutVisibleForSelf success');
  }).catch((err: BusinessError) => {
  console.error(`setShortcutVisibleForSelf errData is errCode:${err.code}  message:${err.message}`);
});
```
