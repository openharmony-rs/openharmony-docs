# setRecoverDisposedRule (System API)

## Modules to Import

```TypeScript
import { appControl } from '@kit.AbilityKit';
```

## setRecoverDisposedRule

```TypeScript
function setRecoverDisposedRule(rule: RecoverDisposedRule): void
```

Sets a recovery disposed rule for current user.

**Since:** 26.1.0

**Required permissions:** ohos.permission.MANAGE_DISPOSED_APP_STATUS

**Model restriction:** This API can be used only in the stage model.

<!--Device-appControl-function setRecoverDisposedRule(rule: RecoverDisposedRule): void--><!--Device-appControl-function setRecoverDisposedRule(rule: RecoverDisposedRule): void-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.AppControl

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rule | [RecoverDisposedRule](arkts-ability-appcontrol-recoverdisposedrule-i-sys.md) | Yes | Recover disposed rule. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied. A non-system application is not allowed to call a system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [17700075](../errorcode-bundle.md#17700075-bundle-name-specified-in-want-is-inconsistent-with-that-of-the-caller) | The specified bundleName of want is not the same with caller. |
| [17700101](../errorcode-bundle.md#17700101-bundle-manager-service-abnormal) | Bundle manager service exception. |
