# setAppShareOptions

## Modules to Import

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## setAppShareOptions

```TypeScript
function setAppShareOptions(intention: Intention, shareOptions: ShareOptions): void
```

Sets the usage scope of the data in the in-app drag-and-drop data channel, as defined by [ShareOptions](arkts-arkdata-unifieddatachannel-shareoptions-e.md). Currently, only the DRAG data channel supports this management setting. After the call succeeds, the usage scope of the data in the in-app drag-and-drop data channel is set to the specified ShareOptions value.

**Since:** 14

**Required permissions:** 
- API version 14 and later: ohos.permission.MANAGE_UDMF_APP_SHARE_OPTION
- API versions 12 to 13: N/A

**Model restriction:** This API can be used only in the stage model.

<!--Device-unifiedDataChannel-function setAppShareOptions(intention: Intention, shareOptions: ShareOptions): void--><!--Device-unifiedDataChannel-function setAppShareOptions(intention: Intention, shareOptions: ShareOptions): void-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| intention | [Intention](arkts-arkdata-unifieddatachannel-intention-e.md) | Yes | Data channel type related to the data operation. Currently, only the DRAG data channel is supported. |
| shareOptions | [ShareOptions](arkts-arkdata-unifieddatachannel-shareoptions-e.md) | Yes | Usage scope of [UnifiedData](arkts-arkdata-unifieddatachannel-unifieddataproperties-c.md) within the device. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | [Sync] Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [20400001](../errorcode-udmf.md#20400001-settings-already-exist) | Settings already exist. To reconfigure, remove the existing sharing options. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API.<br>**Applicable version:** 14 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  unifiedDataChannel.setAppShareOptions(unifiedDataChannel.Intention.DRAG, unifiedDataChannel.ShareOptions.IN_APP);
  console.info(`[UDMF]setAppShareOptions success.`);
} catch (e) {
  let error: BusinessError = e as BusinessError;
  console.error(`[UDMF]setAppShareOptions throws an exception. code is ${error.code}, message is ${error.message}`);
}
```
