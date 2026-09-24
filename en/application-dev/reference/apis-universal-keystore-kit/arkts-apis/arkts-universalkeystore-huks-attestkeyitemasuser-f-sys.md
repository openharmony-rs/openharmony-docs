# attestKeyItemAsUser (System API)

## Modules to Import

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
```

## attestKeyItemAsUser

```TypeScript
function attestKeyItemAsUser(userId: number, keyAlias: string, huksOptions: HuksOptions): Promise<HuksReturnResult>
```

Attests a key for the specified user. This API uses a promise to return the result.

**Since:** 12

**Required permissions:** 
- API version 26 and later: (ohos.permission.ATTEST_KEY and ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS) or (ohos.permission.ENTERPRISE_ATTEST_KEY and ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS)
- API version 11 and later: ohos.permission.ATTEST_KEY and ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability:** SystemCapability.Security.Huks.Extension

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userId | number | Yes | User ID. |
| keyAlias | string | Yes | Alias of the key. The certificate to be obtained stores the key. |
| huksOptions | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | Yes | Options for attesting the key. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[HuksReturnResult](arkts-universalkeystore-huks-huksreturnresult-i.md)&gt; | Promise used to return the result. If the operation is successful, **certChains** in **HuksReturnResult** is the certificate chain obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed: call the attestKeyItemAsUser API, missing Permission: ohos.permission.ATTEST_KEY, or the system has not been unlocked by user, or the user does not exist. |
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

function StringToUint8Array(str: string) {
  let arr: number[] = [];
  for (let i = 0, j = str.length; i < j; ++i) {
    arr.push(str.charCodeAt(i));
  }
  return new Uint8Array(arr);
}

const rsaKeyAlias = 'test_rsaKeyAlias';
const userId = 100;
const userIdStorageLevel = huks.HuksAuthStorageLevel.HUKS_AUTH_STORAGE_LEVEL_CE;

const securityLevel = StringToUint8Array('sec_level');
const challenge = StringToUint8Array('challenge_data');
const versionInfo = StringToUint8Array('version_info');

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

function GetAttestKeyProperties(keyAlias: string): Array<huks.HuksParam> {
  return new Array<huks.HuksParam>({
    tag: huks.HuksTag.HUKS_TAG_ATTESTATION_ID_SEC_LEVEL_INFO,
    value: securityLevel
  }, {
    tag: huks.HuksTag.HUKS_TAG_ATTESTATION_CHALLENGE,
    value: challenge
  }, {
    tag: huks.HuksTag.HUKS_TAG_ATTESTATION_ID_VERSION_INFO,
    value: versionInfo
  }, {
    tag: huks.HuksTag.HUKS_TAG_ATTESTATION_ID_ALIAS,
    value: StringToUint8Array(keyAlias)
  }, {
    tag: huks.HuksTag.HUKS_TAG_AUTH_STORAGE_LEVEL,
    value: userIdStorageLevel,
  })
}

async function LetKeyAttest(keyAlias: string, keyOptions: Array<huks.HuksParam>) {
  let attestOptions: huks.HuksOptions = {
    properties: keyOptions,
  }
  console.info('Start attestation')
  await huks.attestKeyItemAsUser(userId, keyAlias, attestOptions).then((data) => {
    console.info('attestation ok!')
    console.debug(`The obtained certificate chain is ${JSON.stringify(data)}`) // Debugging information. The certificate chain does not need to be printed during the service function development.
    for (let i = 0; data?.certChains?.length && i < data?.certChains?.length; ++i) {
      console.debug(`Certificate ${i} is ${data.certChains[i]}`) // Debugging information. The certificate chain does not need to be printed during the service function development.
    }
    console.info("Attestation successful")
  }).catch((err: BusinessError) => {
    console.error("Attestation failed. Error code: " + err.code +" Error message: "+ err.message)
  })
}

async function TestHuksAttest() {
  await GenerateKey(rsaKeyAlias, GetRSA4096GenerateProperties())
  await LetKeyAttest(rsaKeyAlias, GetAttestKeyProperties(rsaKeyAlias))
}

export default function HuksAsUserTest() {
  console.info('begin huks as user test')
  TestHuksAttest()
}
```
