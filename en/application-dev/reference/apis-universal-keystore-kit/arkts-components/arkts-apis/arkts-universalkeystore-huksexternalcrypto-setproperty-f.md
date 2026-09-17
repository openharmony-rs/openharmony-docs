# setProperty

## Modules to Import

```TypeScript
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
```

## setProperty

```TypeScript
function setProperty(resourceId: string, propertyId: string, params?: HuksExternalCryptoParam[]): Promise<void>
```

The set-type operations of the external crypto extension support calling custom interfaces. However, the custom interface must be registered with the provider.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.Huks.CryptoExtension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resourceId | string | Yes | Indicates the resource ID of the provider. |
| propertyId | string | Yes | Indicates the ID of the property needed to set. Currently supports part of the method names defined in GMT 0016-2023 and self-defined methods registered. |
| params | [HuksExternalCryptoParam](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptoparam-i.md)[] | No | Indicates the operation parameters. This parameter is optional and contains parameters related to the property ID needed to set. |

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
| [12000018](../errorcode-huks.md#12000018-invalid-input-parameter) | The input parameters are invalid. Possible causes: 1. The resourceId or propertyId length is invalid. 2. The parameters contain invalid tags or invalid value types. |
| [12000020](../errorcode-huks.md#12000020-dependent-module-error) | The provider operation failed. This means an error occurred in the crypto extension before calling the UKey driver interface. |
| [12000021](../errorcode-huks.md#12000021-ukey-pin-locked) | The UKey PIN is locked. |
| [12000023](../errorcode-huks.md#12000023-unauthenticated-ukey-pin) | The UKey PIN is not authenticated. |
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

const propertyId = "SKF_SetDevInfo";
const extProperties: Array<huksExternalCrypto.HuksExternalCryptoParam> = [];

async function testFunction() : Promise<void>
{
  try {
    await huksExternalCrypto.setProperty(testResourceId, propertyId, extProperties)
      .then(() => {
        console.info('promise: setProperty success.');
      });
  } catch (error) {
    console.error(`promise: setProperty failed, errCode : ${error.code}, errMsg : ${error.message}`);
  }
}
```
