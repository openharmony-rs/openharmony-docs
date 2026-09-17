# startShortcut (System API)

## Modules to Import

```TypeScript
import { launcherBundleManager } from '@kit.AbilityKit';
```

## startShortcut

```TypeScript
function startShortcut(shortcutInfo: ShortcutInfo, options?: StartOptions): Promise<void>
```

Starts an ability based on the specified shortcut information. This API uses a promise to return the result.

**Since:** 12

**Required permissions:** ohos.permission.START_SHORTCUT

**System capability:** SystemCapability.BundleManager.BundleFramework.Launcher

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| shortcutInfo | [ShortcutInfo](arkts-ability-launcherbundlemanager-shortcutinfo-t.md) | Yes | Shortcut information of the application. |
| options | [StartOptions](arkts-ability-app-ability-startoptions-startoptions-c.md) | No | Startup parameters, which are used to specify the window mode and device ID for switching the mission to the foreground. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Verify permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not support. |
| [17700065](../errorcode-bundle.md#17700065-ability-specified-by-want-in-the-shortcutinfo-struct-cannot-be-started) | The specified shortcut want in shortcut info is not supported to be started. |

**Examples**

```TypeScript
import { launcherBundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data: Array<launcherBundleManager.ShortcutInfo> = launcherBundleManager.getShortcutInfoSync("com.example.demo");
  console.info('data is ' + JSON.stringify(data));
  if (data) {
    try {
      launcherBundleManager.startShortcut(data[0])
        .then(() => {
          console.info('startShortcut success');
        }).catch((err: BusinessError) => {
        console.error(`errData is errCode:${err.code}  message:${err.message}`);
      });
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error(`error is errCode:${code}  message:${message}`);
    }
  }
} catch (errData) {
  let code = (errData as BusinessError).code;
  let message = (errData as BusinessError).message;
  console.error(`errData is errCode:${code}  message:${message}`);
}
```
