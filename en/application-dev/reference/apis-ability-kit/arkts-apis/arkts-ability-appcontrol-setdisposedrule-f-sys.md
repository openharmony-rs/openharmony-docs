# setDisposedRule (System API)

## Modules to Import

```TypeScript
import { appControl } from '@kit.AbilityKit';
```

## setDisposedRule

```TypeScript
function setDisposedRule(appId: string, rule: DisposedRule, appIndex?: number): void
```

Sets the disposed rule for an application or an application clone.

**Since:** 11

**Required permissions:** ohos.permission.MANAGE_DISPOSED_APP_STATUS

<!--Device-appControl-function setDisposedRule(appId: string, rule: DisposedRule, appIndex?: int): void--><!--Device-appControl-function setDisposedRule(appId: string, rule: DisposedRule, appIndex?: int): void-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.AppControl

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| appId | string | Yes | appId or appIdentifier of the application for which the disposed rule is to be set. A disposed rule set using appId overrides the disposed rule set using appIdentifier, and vice versa.<br>**NOTE:** <br> appId is the unique identifier of the application, determined by the application bundle name and signature information. For details about how to obtain it, see [obtain the appId of the application](../../../quick-start/common-problem-of-application.md#how-do-i-obtain-appid-from-application-information). <br> [appIdentifier](../../../reference/apis-ability-kit/js-apis-bundleManager-bundleInfo.md#signatureinfo) is also the unique identifier of the application. For detailed information, see [what is appIdentifier](../../../quick-start/common-problem-of-application.md#what-is-appidentifier). For details about how to obtain it, see [obtain the appIdentifier of the application](../../../quick-start/common-problem-of-application.md#how-do-i-obtain-appidentifier-from-application-information). |
| rule | [DisposedRule](arkts-ability-appcontrol-disposedrule-i-sys.md) | Yes | Disposed rule to set. |
| appIndex | number | No | Index of the application clone. The default value is **0**.<br> The value **0** means to set the disposed rule for the main application. A value greater than 0 means to set the disposed rule for the application clone with the specified index.<br>**Since:** 12 |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied. A non-system application is not allowed to call a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [17700005](../errorcode-bundle.md#17700005-appid-is-an-empty-string) | The specified app ID is invalid. |
| [17700061](../errorcode-bundle.md#17700061-appindex-for-a-clone-is-invalid) | AppIndex is not in the valid range.<br>**Applicable version:** 12 and later |

<!--Del-->
**Examples**

```TypeScript
import { appControl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { Want } from '@kit.AbilityKit';
import { bundleManager } from '@kit.AbilityKit';

let appId = "com.example.myapplication_xxxxx";
let want: Want = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  abilityName: "EntryAbility"
};
let elementName: bundleManager.ElementName = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  abilityName: "EntryAbility"
};
let rule: appControl.DisposedRule = {
  want: want,
  componentType: appControl.ComponentType.UI_ABILITY,
  disposedType: appControl.DisposedType.BLOCK_APPLICATION,
  controlType: appControl.ControlType.ALLOWED_LIST,
  elementList: [
    elementName
  ],
  priority: 100,
  pageJump: appControl.PageJumpMode.PAGE_JUMP_WINDOW_SHOW
};

try {
  appControl.setDisposedRule(appId, rule, 1);
} catch (error) {
  let message = (error as BusinessError).message;
  console.error('setDisposedRule failed ' + message);
}
```

<!--DelEnd-->
