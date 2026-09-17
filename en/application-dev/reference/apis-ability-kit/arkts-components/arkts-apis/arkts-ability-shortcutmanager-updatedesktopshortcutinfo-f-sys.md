# updateDesktopShortcutInfo (System API)

## Modules to Import

```TypeScript
import { shortcutManager } from '@kit.AbilityKit';
```

## updateDesktopShortcutInfo

```TypeScript
function updateDesktopShortcutInfo(shortcutInfo: ShortcutInfo, userId: number): Promise<void>
```

Updates a shortcut for the given user. This API uses a promise to return the result.

**Since:** 26.1.0

**Required permissions:** ohos.permission.MANAGE_SHORTCUTS or (ohos.permission.MANAGE_SHORTCUTS and ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS)

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BundleManager.BundleFramework.Launcher

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| shortcutInfo | [ShortcutInfo](arkts-ability-shortcutmanager-shortcutinfo-t.md) | Yes | Shortcut information. |
| userId | number | Yes | User ID, which can be obtained by calling [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Verify permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundle name is not found. |
| [17700004](../errorcode-bundle.md#17700004-user-id-does-not-exist) | The specified user ID is not found. |
| [17700026](../errorcode-bundle.md#17700026-bundle-disabled) | The specified bundle is disabled. |
| [17700061](../errorcode-bundle.md#17700061-appindex-for-a-clone-is-invalid) | The specified app index is invalid. |
| 18100002 | The specified shortcut to be updated is not found. |

**Examples**

```TypeScript
import { shortcutManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

// Replace with the actual shortcut information and user ID.
let shortcutInfo: shortcutManager.ShortcutInfo = {
  id: 'test1',
  bundleName: 'com.example.myapplication',
  moduleName: '',
  hostAbility: '',
  icon: '',
  iconId: 1,
  label: 'hello',
  labelId: 1,
  wants: [],
  appIndex: 0,
  sourceType: 0,
};

try {
  shortcutManager.updateDesktopShortcutInfo(shortcutInfo, 100)
    .then(() => {
      hilog.info(0x0000, 'testTag', 'updateDesktopShortcutInfo successfully');
    }).catch((err: Error) => {
      hilog.error(0x0000, 'testTag', 'updateDesktopShortcutInfo failed. Cause: %{public}s', err.message);
    });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'updateDesktopShortcutInfo failed. Cause: %{public}s', message);
}
```
