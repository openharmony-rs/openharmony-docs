# setAppShareOptions

## Modules to Import

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## setAppShareOptions

```TypeScript
function setAppShareOptions(intention: Intention, shareOptions: ShareOptions): void
```

Sets the [ShareOptions](arkts-arkdata-unifieddatachannel-shareoptions-e.md) for the application data. Currently, only the drag- and-drop data channel is supported.

**Since:** 14

**Required permissions:** 
- API version 14 and later: ohos.permission.MANAGE_UDMF_APP_SHARE_OPTION
- API versions 12 to 13: N/A

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| intention | [Intention](arkts-arkdata-unifieddatachannel-intention-e.md) | Yes | Type of the data channel. Currently, only the data channel of the **DRAG** type is supported. |
| shareOptions | [ShareOptions](arkts-arkdata-unifieddatachannel-shareoptions-e.md) | Yes | Usage scope of the [UnifiedData](arkts-arkdata-unifieddatachannel-unifieddataproperties-c.md). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 - 13 |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
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
