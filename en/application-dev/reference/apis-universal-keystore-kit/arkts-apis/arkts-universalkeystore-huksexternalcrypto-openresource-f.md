# openResource

## Modules to Import

```TypeScript
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
```

## openResource

```TypeScript
function openResource(resourceId: string, params?: HuksExternalCryptoParam[]): Promise<void>
```

Open resource by specific resource ID. NOTE: The opened resource must be closed using closeResource.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.Huks.CryptoExtension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resourceId | string | Yes | Indicates the resource ID of the provider. |
| params | [HuksExternalCryptoParam](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptoparam-i.md)[] | No | Indicates the input operation parameters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Return value of the Promise type |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability. 2. The chip does not support the capability. 3. A dependent service feature is not supported. |
| [12000005](../errorcode-huks.md#12000005-ipc-error) | IPC communication failed. |
| [12000006](../errorcode-huks.md#12000006-algorithm-library-operation-failed) | Failed to call the UKey driver interface. Please check the UKey connection and driver status. |
| [12000011](../errorcode-huks.md#12000011-the-entity-does-not-exist) | The cached resource ID is not found. This may happen because the resource ID has not been opened. |
| [12000012](../errorcode-huks.md#12000012-external-error) | Device environment or input parameters are abnormal. This error may occur if the process function is not found, or due to other issues. |
| [12000014](../errorcode-huks.md#12000014-insufficient-memory) | The memory is insufficient. |
| [12000017](../errorcode-huks.md#12000017-duplicate-key-alias) | The resource with the resource ID is already open. |
| [12000018](../errorcode-huks.md#12000018-invalid-input-parameter) | Input parameters are invalid. Possible causes: 1. The resourceId length is invalid. 2. The parameters contain invalid tags or invalid value types. |
| [12000020](../errorcode-huks.md#12000020-dependent-module-error) | The provider operation failed. This means an error occurred in the crypto extension before calling the UKey driver interface. |
| [12000024](../errorcode-huks.md#12000024-device-or-resource-busy) | The provider or UKey is busy. |
| [12000025](../errorcode-huks.md#12000025-resource-limit-exceeded) | The opened resources exceed the limit. |

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

huksExternalCrypto.openResource(testResourceId)
    .then(() => {
      console.info('promise: openResource success.');
    });
```
