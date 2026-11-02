# removeAppShareOptions

## Modules to Import

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## removeAppShareOptions

```TypeScript
function removeAppShareOptions(intention: Intention): void
```

Clears the control information set by [setAppShareOptions](arkts-arkdata-unifieddatachannel-setappshareoptions-f.md). After this API is called successfully, the control information set by setAppShareOptions is cleared, and the in-app drag-and-drop channel data is restored to the default usage scope.

**Since:** 14

**Required permissions:** 
- API version 14 and later: ohos.permission.MANAGE_UDMF_APP_SHARE_OPTION
- API versions 12 to 13: N/A

**Model restriction:** This API can be used only in the stage model.

<!--Device-unifiedDataChannel-function removeAppShareOptions(intention: Intention): void--><!--Device-unifiedDataChannel-function removeAppShareOptions(intention: Intention): void-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| intention | [Intention](arkts-arkdata-unifieddatachannel-intention-e.md) | Yes | Data channel type related to the data operation. Currently, only the DRAG data channel is supported. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | [Sync] Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API.<br>**Applicable version:** 14 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  unifiedDataChannel.removeAppShareOptions(unifiedDataChannel.Intention.DRAG);
  console.info(`[UDMF]removeAppShareOptions success.`);
} catch (e) {
  let error: BusinessError = e as BusinessError;
  console.error(`[UDMF]removeAppShareOptions throws an exception. code is ${error.code}, message is ${error.message}`);
}
```
