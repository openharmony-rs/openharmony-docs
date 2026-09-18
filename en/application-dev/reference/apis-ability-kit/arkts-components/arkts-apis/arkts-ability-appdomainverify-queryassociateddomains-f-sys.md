# queryAssociatedDomains (System API)

## Modules to Import

```TypeScript
import { appDomainVerify } from '@kit.AbilityKit';
```

## queryAssociatedDomains

```TypeScript
function queryAssociatedDomains(bundleName: string): string[]
```

query domains verify associated with bundleName.

**Since:** 13

**Required permissions:** ohos.permission.GET_APP_DOMAIN_BUNDLE_INFO

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BundleManager.AppDomainVerify

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | app bundleName. |

**Return value:**

| Type | Description |
| --- | --- |
| string[] | Result domains. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | System API accessed by non-system app. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [29900001](../errorcode-appDomainVerify-sys.md#29900001-internal-system-service-error) | Internal error. |

**Examples**

```TypeScript
import { appDomainVerify } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

// Obtain the list of domain names associated with the bundle name "com.example.app1".
let bundleName = "com.example.app1";
let domains = appDomainVerify.queryAssociatedDomains(bundleName);
domains.forEach(domain => {
  hilog.info(0x0000, 'testTag', `app:${bundleName} associate with domain:${domain}`);
});
```
