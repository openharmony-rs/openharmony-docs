# clearUkeyPinAuthState

## Modules to Import

```TypeScript
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
```

## clearUkeyPinAuthState

```TypeScript
function clearUkeyPinAuthState(resourceId: string): Promise<void>
```

Clear the PIN auth state of the specified resource ID.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.Huks.CryptoExtension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resourceId | string | Yes | Indicates the resource ID of the provider. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | The promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability. 2. The chip does not support the capability. 3. A dependent service feature is not supported. |
| [12000005](../errorcode-huks.md#12000005-ipc-error) | IPC communication failed. |
| [12000006](../errorcode-huks.md#12000006-algorithm-library-operation-failed) | Failed to call the UKey driver interface. Please check the UKey connection and driver status. |
| [12000011](../errorcode-huks.md#12000011-the-entity-does-not-exist) | The cached resource ID not found. |
| [12000012](../errorcode-huks.md#12000012-external-error) | Device environment or input parameters are abnormal. This may occur if the process function is null, or due to other issues. |
| [12000014](../errorcode-huks.md#12000014-insufficient-memory) | The memory is insufficient. |
| [12000018](../errorcode-huks.md#12000018-invalid-input-parameter) | The input parameters are invalid. Possible causes: 1. The resourceId length is invalid. |
| [12000020](../errorcode-huks.md#12000020-dependent-module-error) | The provider operation failed. This means an error occurred in the crypto extension before calling the UKey driver interface. |
| [12000024](../errorcode-huks.md#12000024-device-or-resource-busy) | The provider or UKey is busy. |

**Examples**

```TypeScript
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';

const testResourceId = JSON.stringify({
  providerName: "testProviderName",
  bundleName: "com.example.cryptoapplication",
  abilityName: "CryptoExtension",
  index: {
    key: "testKey"
  } as ESObject
});

huksExternalCrypto.clearUkeyPinAuthState(testResourceId)
    .then(() => {
      console.info('promise: clearUkeyPinAuthState success.');
    });
```
