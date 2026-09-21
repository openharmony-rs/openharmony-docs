# anonAttestKeyItemOfflineAsUser (System API)

## Modules to Import

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
```

## anonAttestKeyItemOfflineAsUser

```TypeScript
function anonAttestKeyItemOfflineAsUser(userId: number, keyAlias: string,
      params: HuksParam[]): Promise<HuksReturnResult>
```

Obtains an anonymous key certificate in offline mode for a specified user. This API uses a promise to return the result.

> **NOTE:** 
> 
> - Offline key attestation depends on the network. You need to periodically connect to the network to use this API to update the offline certificate.
> 
> - Offline anonymous key attestation requires that the local time be accurate. Otherwise, the peer end may fail to verify the certificate expiration.

**Since:** 26.0.0

**Required permissions:** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.Huks.Extension

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userId | number | Yes | User ID<br>The value range is all integers. |
| keyAlias | string | Yes | Alias of the key. The certificate to be obtained stores the key. |
| params | [HuksParam](arkts-universalkeystore-huks-huksparam-i.md)[] | Yes | Options for attesting the key. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[HuksReturnResult](arkts-universalkeystore-huks-huksreturnresult-i.md)&gt; | Promise used to return the result. When the call is successful, the **certChains** member of the **HuksReturnResult** object is the obtained certificate chain. Otherwise, the member is empty. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed: call the anonAttestKeyItemOfflineAsUser API, missing Permission: ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS, or the system is not unlocked by the user, or the user does not exist. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system apps use system APIs. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability. 2. The chip does not support the capability. 3. A dependent service feature is not supported. |
| [12000001](../errorcode-huks.md#12000001-feature-not-supported) | The function is not supported. Possible causes: 1. The algorithm mode is not supported. 2. The group key is not supported. 3. The extended encryption key is not supported. |
| [12000002](../errorcode-huks.md#12000002-missing-key-algorithm-parameter) | The algorithm parameter is missing. |
| [12000003](../errorcode-huks.md#12000003-invalid-key-algorithm-parameter) | The algorithm parameter is invalid. |
| [12000004](../errorcode-huks.md#12000004-file-error) | The file operation failed. |
| [12000005](../errorcode-huks.md#12000005-ipc-error) | The IPC communication failed. |
| [12000006](../errorcode-huks.md#12000006-algorithm-library-operation-failed) | The encryption engine is faulty. |
| [12000011](../errorcode-huks.md#12000011-the-entity-does-not-exist) | The queried entity does not exist. |
| [12000012](../errorcode-huks.md#12000012-external-error) | The device environment or input parameter is abnormal. |
| [12000014](../errorcode-huks.md#12000014-insufficient-memory) | The memory is insufficient. |
| [12000018](../errorcode-huks.md#12000018-invalid-input-parameter) | The parameter is incorrect. Possible causes: 1. A mandatory parameter is left empty. 2. The parameter type is incorrect. 3. The parameter verification failed. |
| [12000024](../errorcode-huks.md#12000024-device-or-resource-busy) | The operation times out. This may be caused by network jitter. You can try again later. |
| 12000027 | The network is unavailable. Check network connections. |

**Examples**

Prerequisites: see Example of generateKeyItemAsUser.

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
import { BusinessError } from "@kit.BasicServicesKit"

function StringToUint8Array(str: string) {
  let arr: number[] = [];
  for (let i = 0, j = str.length; i < j; ++i) {
    arr.push(str.charCodeAt(i));
  }
  return new Uint8Array(arr);
}

const userId = 100;
const userIdStorageLevel = huks.HuksAuthStorageLevel.HUKS_AUTH_STORAGE_LEVEL_CE;
const keyAliasString = "key anon local attest as user";

const challenge = StringToUint8Array('challenge_data');

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
    },
    {
      tag: huks.HuksTag.HUKS_TAG_AUTH_STORAGE_LEVEL,
      value: userIdStorageLevel,
    }
  ];
  let options: huks.HuksOptions = {
    properties: properties
  };

  await huks.generateKeyItemAsUser(userId, alias, options);
}

async function anonAttestKeyItemOfflineAsUser() {
  let aliasString = keyAliasString;
  let aliasUint8 = StringToUint8Array(aliasString);
  let properties: Array<huks.HuksParam> = [
    {
      tag: huks.HuksTag.HUKS_TAG_ATTESTATION_CHALLENGE,
      value: challenge
    },
    {
      tag: huks.HuksTag.HUKS_TAG_ATTESTATION_ID_ALIAS,
      value: aliasUint8
    },
    {
      tag: huks.HuksTag.HUKS_TAG_AUTH_STORAGE_LEVEL,
      value: userIdStorageLevel,
    }
  ];

  await generateKey(aliasString);
  await huks.anonAttestKeyItemOfflineAsUser(userId, aliasString, properties).then((data) => {
    console.info('anonAttestationOffline ok!')
    console.debug(`'CERT:${JSON.stringify(data)}`)
    for (let i = 0; data?.certChains?.length && i < data?.certChains?.length; ++i) {
      console.info(`CERT${i} is ${data.certChains[i]}`)
    }
    console.info("anonAttestationOffline Success")
  }).catch((err: BusinessError) => {
    console.error("anonAttestationOffline fail, erroCode: " + err.code + " erroInfo: " + err.message)
  })
}
```
