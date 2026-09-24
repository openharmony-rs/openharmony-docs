# getProperty

## Modules to Import

```TypeScript
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
```

## getProperty

```TypeScript
function getProperty(resourceId: string, propertyId: string, params?: Array<HuksExternalCryptoParam>): Promise<Array<HuksExternalCryptoParam>>
```

Obtains a property value. This API uses a promise to return the result.

The **propertyId** indicates the ID of the property to be queried. Currently, only the SKF API names defined in GMT 0016-2023 can be used as property IDs. The supported IDs are as follows:

- SKF_EnumDev  
- SKF_GetDevInfo  
- SKF_EnumApplication  
- SKF_EnumContainer

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.Huks.CryptoExtension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resourceId | string | Yes | Resource ID, which can be obtained using [certificateManagerDialog.openAuthorizeDialog22+](../../apis-device-certificate-kit/arkts-apis/arkts-devicecertificate-certificatemanagerdialog-openauthorizedialog-f.md#openauthorizedialog-1). The result contains **resourceId**. |
| propertyId | string | Yes | Property name for the search operation, which is the SKF API name defined in GMT 0016-2023. You need to make adaptation based on the API name. |
| params | Array&lt;[HuksExternalCryptoParam](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptoparam-i.md)&gt; | No | Parameters to be passed to [Extension Ability](arkts-universalkeystore-security-cryptoextensionability-cryptoextensionability-c.md). If a non-system application passes [HUKS_EXT_CRYPTO_TAG_UID](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptotagtype-e.md), the parameter is invalid. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[HuksExternalCryptoParam](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptoparam-i.md)&gt;&gt; | Promise that returns the operation result. If the call is successful, an array of the **HuksExternalCryptoParam** type is returned, containing the properties to be queried. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability. 2. The chip does not support the capability. 3. A dependent service feature is not supported. |
| [12000005](../errorcode-huks.md#12000005-ipc-error) | IPC communication failed. |
| [12000006](../errorcode-huks.md#12000006-algorithm-library-operation-failed) | If the UKey driver operation failed. Possible causes: 1. Error reported when the provider accesses the SKF interface of UKey. |
| [12000011](../errorcode-huks.md#12000011-the-entity-does-not-exist) | If the cached resource ID is not found. |
| [12000012](../errorcode-huks.md#12000012-external-error) | Device environment or input parameter is abnormal. This error may occur if the process function is not found, or due to other issues. |
| [12000014](../errorcode-huks.md#12000014-insufficient-memory) | If the memory is insufficient. |
| [12000018](../errorcode-huks.md#12000018-invalid-input-parameter) | Input parameter is invalid. Possible causes: 1. The resourceId or propertyId length is invalid. 2. The params contains invalid tags or invalid value types. |
| [12000020](../errorcode-huks.md#12000020-dependent-module-error) | If the provider operation failed. Possible causes: 1. The provider experienced an internal processing error. |
| [12000021](../errorcode-huks.md#12000021-ukey-pin-locked) | The UKey PIN is locked. |
| [12000023](../errorcode-huks.md#12000023-unauthenticated-ukey-pin) | The UKey PIN is not authenticated. |
| [12000024](../errorcode-huks.md#12000024-device-or-resource-busy) | If the provider or UKey is busy. |

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

let propertyId = "SKF_EnumDev";
const extProperties: Array<huksExternalCrypto.HuksExternalCryptoParam> = [];

console.info('promise: await huksExternalCrypto getProperty.');
async function testFunction() : Promise<void>
{
  try {
    await huksExternalCrypto.getProperty(testResourceId, propertyId, extProperties)
      .then((data) => {
        console.info(`promise: getProperty success, data: ` + JSON.stringify(data));
      });
  } catch (error) {
    console.error(`promise: getProperty failed, errCode : ${error.code}, errMsg : ${error.message}`);
  }
}
```
