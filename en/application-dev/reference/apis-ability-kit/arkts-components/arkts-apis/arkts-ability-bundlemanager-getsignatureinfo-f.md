# getSignatureInfo

## Modules to Import

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## getSignatureInfo

```TypeScript
function getSignatureInfo(uid: number): SignatureInfo
```

Obtains the [signature information](arkts-ability-bundleinfo-signatureinfo-i.md) of an application based on the given UID.

**Since:** 18

**Required permissions:** ohos.permission.GET_SIGNATURE_INFO

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uid | number | Yes | UID of the application. |

**Return value:**

| Type | Description |
| --- | --- |
| [SignatureInfo](arkts-ability-bundlemanager-signatureinfo-t.md) | SignatureInfo object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [17700021](../errorcode-bundle.md#17700021-invalid-uid) | The uid is not found. |

**Examples**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let uid = 20010005; // Replace uid with the UID of the corresponding application.
try {
  let data = bundleManager.getSignatureInfo(uid);
  hilog.info(0x0000, 'testTag', 'getSignatureInfo successfully. Data: %{public}s', JSON.stringify(data));
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getSignatureInfo failed. Cause: %{public}s', message);
}
```
