# anonAttestKeyItemOffline

## Modules to Import

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
```

## anonAttestKeyItemOffline

```TypeScript
function anonAttestKeyItemOffline(keyAlias: string, params: HuksParam[]): Promise<HuksReturnResult>
```

Obtains an anonymous key certificate in offline mode. This API uses a promise to return the result.

> **NOTE:** 
> 
> 
> - Offline key attestation depends on the network. You need to periodically connect to the network to use this API to update the offline certificate. Offline anonymous key attestation is recommended.
> 
> 
> - Offline anonymous key attestation requires that the local time be accurate. Otherwise, the peer end may fail to verify the certificate expiration.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Security.Huks.Extension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keyAlias | string | Yes | Alias of the key. The certificate to be obtained stores the key. |
| params | [HuksParam](arkts-universalkeystore-huks-huksparam-i.md)[] | Yes | Parameters and data required for obtaining the certificate. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[HuksReturnResult](arkts-universalkeystore-huks-huksreturnresult-i.md)&gt; | Promise that returns the operation result. When the call is successful, the **certChains** member of **HuksReturnResult** is the obtained certificate chain. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability. 2. The chip does not support the capability. 3. A dependent service feature is not supported. |
| [12000001](../errorcode-huks.md#12000001-feature-not-supported) | The algorithm mode is not supported. |
| [12000004](../errorcode-huks.md#12000004-file-error) | The file operation failed. |
| [12000005](../errorcode-huks.md#12000005-ipc-error) | The IPC communication failed. |
| [12000006](../errorcode-huks.md#12000006-algorithm-library-operation-failed) | The encryption engine is faulty. |
| [12000011](../errorcode-huks.md#12000011-the-entity-does-not-exist) | The queried entity does not exist. |
| [12000012](../errorcode-huks.md#12000012-external-error) | The device environment or input parameter is abnormal. |
| [12000014](../errorcode-huks.md#12000014-insufficient-memory) | The memory is insufficient. |
| [12000018](../errorcode-huks.md#12000018-invalid-input-parameter) | The parameter is incorrect. Possible causes: 1. A mandatory parameter is left empty. 2. The parameter type is incorrect. 3. The parameter verification failed. 4. The group ID specified by the access group tag is invalid. |
| [12000024](../errorcode-huks.md#12000024-device-or-resource-busy) | The operation times out. This may be caused by network jitter. You can try again later. |
| 12000027 | The network is unavailable. Check network connections. |

**Examples**

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';

function stringToUint8Array(str: string): Uint8Array {
  let arr: number[] = [];
  for (let i = 0, j = str.length; i < j; ++i) {
    arr.push(str.charCodeAt(i));
  }
  let tmpUint8Array = new Uint8Array(arr);
  return tmpUint8Array;
}

let challenge = stringToUint8Array('challenge_data');
let keyAliasString = "key anon local attest";

async function generateKey(alias: string) {
  let properties: Array<huks.HuksParam> = [
    {
      tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
      value: huks.HuksKeyAlg.HUKS_ALG_ECC
    },
    {
      tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
      value: huks.HuksKeySize.HUKS_ECC_KEY_SIZE_256
    },
    {
      tag: huks.HuksTag.HUKS_TAG_PURPOSE,
      value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_SIGN | huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_VERIFY
    },
    {
      tag: huks.HuksTag.HUKS_TAG_DIGEST,
      value: huks.HuksKeyDigest.HUKS_DIGEST_SHA256
    },
    {
      tag: huks.HuksTag.HUKS_TAG_PADDING,
      value: huks.HuksKeyPadding.HUKS_PADDING_NONE
    }
  ];
  let options: huks.HuksOptions = {
    properties: properties
  };

  await huks.generateKeyItem(alias, options);
}

async function anonAttestKeyOffline() {
  let aliasString = keyAliasString;
  let aliasUint8 = stringToUint8Array(aliasString);
  let properties: Array<huks.HuksParam> = [
    {
      tag: huks.HuksTag.HUKS_TAG_ATTESTATION_CHALLENGE,
      value: challenge
    },
    {
      tag: huks.HuksTag.HUKS_TAG_ATTESTATION_ID_ALIAS,
      value: aliasUint8
    }
  ];

  await generateKey(aliasString);
  await huks.anonAttestKeyItemOffline(aliasString, properties);
}
```
