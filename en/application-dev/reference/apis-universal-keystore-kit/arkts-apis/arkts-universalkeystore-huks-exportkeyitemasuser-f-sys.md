# exportKeyItemAsUser (System API)

## Modules to Import

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
```

## exportKeyItemAsUser

```TypeScript
function exportKeyItemAsUser(userId: number, keyAlias: string, huksOptions: HuksOptions): Promise<HuksReturnResult>
```

Exports the public key for the specified user. This API uses a promise to return the result.

**Since:** 12

**Required permissions:** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability:** SystemCapability.Security.Huks.Extension

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userId | number | Yes | User ID. |
| keyAlias | string | Yes | Key alias, which must be the same as the alias used when the key was generated. |
| huksOptions | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | Yes | Empty object (leave this parameter empty). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[HuksReturnResult](arkts-universalkeystore-huks-huksreturnresult-i.md)&gt; | Promise used to return the result. If the operation is successful, **outData** in **HuksReturnResult** is the public key exported. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed: call the exportKeyItemAsUser API, missing Permission: ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS, or the system has not been unlocked by user, or the user does not exist. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | non-system applications are not allowed to use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability. 2. The chip does not support the capability. 3. A dependent service feature is not supported. |
| [12000001](../errorcode-huks.md#12000001-feature-not-supported) | Feature is not supported. Possible causes: 1. The algorithm mode is not supported. 2. The group key is not supported. 3. The crypto extension key is not supported. |
| [12000002](../errorcode-huks.md#12000002-missing-key-algorithm-parameter) | algorithm param is missing |
| [12000003](../errorcode-huks.md#12000003-invalid-key-algorithm-parameter) | algorithm param is invalid |
| [12000004](../errorcode-huks.md#12000004-file-error) | operating file failed |
| [12000005](../errorcode-huks.md#12000005-ipc-error) | IPC communication failed |
| [12000006](../errorcode-huks.md#12000006-algorithm-library-operation-failed) | error occurred in crypto engine |
| [12000011](../errorcode-huks.md#12000011-the-entity-does-not-exist) | queried entity does not exist |
| [12000012](../errorcode-huks.md#12000012-external-error) | Device environment or input parameter abnormal |
| [12000014](../errorcode-huks.md#12000014-insufficient-memory) | memory is insufficient |

**Examples**

Prerequisites: see Example of generateKeyItemAsUser.

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
import { BusinessError } from "@kit.BasicServicesKit"

const rsaKeyAlias = 'test_rsaKeyAlias';
const userId = 100;
const userIdStorageLevel = huks.HuksAuthStorageLevel.HUKS_AUTH_STORAGE_LEVEL_CE;

function GetRSA4096GenerateProperties(): Array<huks.HuksParam> {
  return [{
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_RSA
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_RSA_KEY_SIZE_4096
  }, {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT |
    huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_DECRYPT
  }, {
    tag: huks.HuksTag.HUKS_TAG_DIGEST,
    value: huks.HuksKeyDigest.HUKS_DIGEST_SHA256
  }, {
    tag: huks.HuksTag.HUKS_TAG_PADDING,
    value: huks.HuksKeyPadding.HUKS_PADDING_PKCS1_V1_5
  }, {
    tag: huks.HuksTag.HUKS_TAG_BLOCK_MODE,
    value: huks.HuksCipherMode.HUKS_MODE_ECB
  }, {
    tag: huks.HuksTag.HUKS_TAG_AUTH_STORAGE_LEVEL,
    value: userIdStorageLevel,
  }]
}

async function GenerateKey(keyAlias: string, genProperties: Array<huks.HuksParam>) {
  const options: huks.HuksOptions = {
    properties: genProperties
  }
  await huks.generateKeyItemAsUser(userId, keyAlias, options).then((data) => {
    console.info("Generated a key with alias of: " + keyAlias + "")
  }).catch((err: BusinessError) => {
    console.error("Failed to generate the key. Error code: " + err.code + " Error message: " + err.message)
  })
}

async function ExportPublicKey(keyAlias: string) {
  const options: huks.HuksOptions = {
    properties: [{
      tag: huks.HuksTag.HUKS_TAG_AUTH_STORAGE_LEVEL,
      value: userIdStorageLevel,
    }]
  }
  await huks.exportKeyItemAsUser(userId, keyAlias, options).then((data) => {
    console.info("Exported the public key with the alias of: " + keyAlias + ". The data length is " + data?.outData?.length)
  }).catch((err: BusinessError) => {
    console.error("Failed to export the key. Error code: " + err.code + " Error message: " + err.message)
  })
}

async function ExportHuksTest() {
  await GenerateKey(rsaKeyAlias, GetRSA4096GenerateProperties())
  await ExportPublicKey(rsaKeyAlias)
}

export default function HuksAsUserTest() {
  console.info('begin huks as user test')
  ExportHuksTest()
}
```
