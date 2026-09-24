# importWrappedKeyItem

## Modules to Import

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
```

## importWrappedKeyItem

```TypeScript
function importWrappedKeyItem(
    keyAlias: string,
    wrappingKeyAlias: string,
    options: HuksOptions,
    callback: AsyncCallback<void>
  ): void
```

Imports keys in secure mode. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> Importing SE security level wrapped keys defined in [HuksKeySecurityLevel](arkts-universalkeystore-huks-hukskeysecuritylevel-e.md)
> requires the ohos.permission.ACCESS_SE_KEY permission.

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** 
- API version 12 and later: SystemCapability.Security.Huks.Core
- API versions 9 to 11: SystemCapability.Security.Huks.Extension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keyAlias | string | Yes | Alias of the wrapped key to import. |
| wrappingKeyAlias | string | Yes | Alias of the data used to unwrap the key imported. |
| options | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | Yes | Tags required for the import and the wrapped key to import. The algorithm, key purpose, and key length are mandatory. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, no **err** value is returned; otherwise, an error code is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed: call the importWrappedKeyItem API, missing Permission: ohos.permission.ACCESS_SE_KEY.<br>**Applicable version:** 26.0.0 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability. 2. The chip does not support the capability. 3. A dependent service feature is not supported. |
| [12000001](../errorcode-huks.md#12000001-feature-not-supported) | algorithm mode is not supported |
| [12000002](../errorcode-huks.md#12000002-missing-key-algorithm-parameter) | algorithm param is missing |
| [12000003](../errorcode-huks.md#12000003-invalid-key-algorithm-parameter) | algorithm param is invalid |
| [12000004](../errorcode-huks.md#12000004-file-error) | operating file failed |
| [12000005](../errorcode-huks.md#12000005-ipc-error) | IPC communication failed |
| [12000006](../errorcode-huks.md#12000006-algorithm-library-operation-failed) | error occurred in crypto engine |
| [12000011](../errorcode-huks.md#12000011-the-entity-does-not-exist) | queried entity does not exist |
| [12000012](../errorcode-huks.md#12000012-external-error) | Device environment or input parameter abnormal |
| [12000013](../errorcode-huks.md#12000013-the-credential-does-not-exist) | queried credential does not exist |
| [12000014](../errorcode-huks.md#12000014-insufficient-memory) | memory is insufficient |
| [12000015](../errorcode-huks.md#12000015-failed-to-invoke-other-system-services) | Failed to obtain the security information via UserIAM |
| [12000017](../errorcode-huks.md#12000017-duplicate-key-alias) | The key with the same alias already exists<br>**Applicable version:** 20 and later |
| [12000018](../errorcode-huks.md#12000018-invalid-input-parameter) | the group id specified by the access group tag is invalid<br>**Applicable version:** 23 and later |
| [12000020](../errorcode-huks.md#12000020-dependent-module-error) | the provider operation failed<br>**Applicable version:** 26.0.0 and later |
| [12000021](../errorcode-huks.md#12000021-ukey-pin-locked) | the UKey PIN is locked<br>**Applicable version:** 26.0.0 and later |
| [12000023](../errorcode-huks.md#12000023-unauthenticated-ukey-pin) | the UKey PIN not authenticated<br>**Applicable version:** 26.0.0 and later |
| [12000024](../errorcode-huks.md#12000024-device-or-resource-busy) | the provider or UKey is busy<br>**Applicable version:** 26.0.0 and later |
| [12000026](../errorcode-huks.md#12000026-secure-element-fault) | the secure element is not available<br>**Applicable version:** 26.0.0 and later |

**Examples**

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';

let alias1 = "importAlias";
let alias2 = "wrappingKeyAlias";

async function TestGenFunc(alias: string, options: huks.HuksOptions) {
  await genKey(alias, options)
    .then(() => {
      console.info(`callback: generateKeyItem success`);
    });
}

function genKey(alias: string, options: huks.HuksOptions) {
  return new Promise<void>((resolve, reject) => {
    huks.generateKeyItem(alias, options, (error, data) => {
      if (error) {
        reject(error);
      } else {
        resolve(data);
      }
    });
  });
}

async function TestExportFunc(alias: string, options: huks.HuksOptions) {
  await exportKey(alias, options)
    .then((data) => {
      console.info(`callback: exportKeyItem success, data = ${JSON.stringify(data)}`);
    });
}

function exportKey(alias: string, options: huks.HuksOptions) {
  return new Promise<huks.HuksReturnResult>((resolve, reject) => {
    huks.exportKeyItem(alias, options, (error, data) => {
      if (error) {
        reject(error);
      } else {
        resolve(data);
      }
    });
  });
}

async function TestImportWrappedFunc(alias: string, wrappingAlias: string, options: huks.HuksOptions) {
  await importWrappedKey(alias, wrappingAlias, options)
    .then(() => {
      console.info(`callback: importWrappedKeyItem success`);
    });
}

function importWrappedKey(alias: string, wrappingAlias: string, options: huks.HuksOptions) {
  return new Promise<void>((resolve, reject) => {
    huks.importWrappedKeyItem(alias, wrappingAlias, options, (error, data) => {
      if (error) {
        reject(error);
      } else {
        resolve(data);
      }
    });
  });
}

async function TestImportWrappedKeyFunc(
  alias: string,
  wrappingAlias: string,
  genOptions: huks.HuksOptions,
  importOptions: huks.HuksOptions
) {
  await TestGenFunc(wrappingAlias, genOptions);
  await TestExportFunc(wrappingAlias, genOptions);

  /* The following operation does not involve calling of HUKS APIs, and the specific implementation is not provided here.
   * For example, import keyA.
   * 1. Use ECC to generate a public and private key pair named keyB. The public key is keyB_pub, and the private key is keyB_pri.
   * 2. Use keyB_pri and the public key obtained from wrappingAlias to negotiate the shared key share_key.
   * 3. Randomly generate a key kek and use it to encrypt keyA with AES-GCM. During the encryption, record nonce1, aad1, ciphertext keyA_enc, and encrypted tag1.
   * 4. Use share_key to encrypt kek with AES-GCM. During the encryption, record nonce2, aad2, ciphertext kek_enc, and encrypted tag2.
   * 5. Generate the **importOptions.inData** field in the following format:
   *     keyB_pub length (4 bytes) + keyB_pub + aad2 length (4 bytes) + aad2 +
   *     Length of nonce2 (4 bytes) + Data of nonce2 + Length of tag2 (4 bytes) + Data of tag2 +
   *     Length of kek_enc (4 bytes) + Data of kek_enc + Length of aad1 (4 bytes) + Data of aad1 +
   *     Length of nonce1 (4 bytes) + Data of nonce1 + Length of tag1 (4 bytes) + Data of tag1 +
   *     Length of keyA (4 bytes) + Length of keyA + Length of keyA_enc (4 bytes) + Data of keyA_enc
   */
  /* The key data imported may be different from the sample code given below. The data structure is described in the preceding comments. */
  let inputKey = new Uint8Array([0x02, 0x00, 0x00, 0x00]);
  importOptions.inData = inputKey;
  await TestImportWrappedFunc(alias, wrappingAlias, importOptions);
}

function makeGenerateOptions() {
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
      value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_UNWRAP
    },
    {
      tag: huks.HuksTag.HUKS_TAG_DIGEST,
      value: huks.HuksKeyDigest.HUKS_DIGEST_SHA256
    },
    {
      tag: huks.HuksTag.HUKS_TAG_IMPORT_KEY_TYPE,
      value: huks.HuksImportKeyType.HUKS_KEY_TYPE_KEY_PAIR,
    }
  ];
  let options: huks.HuksOptions = {
    properties: properties
  };
  return options;
};

function makeImportOptions() {
  let properties: Array<huks.HuksParam> = [
    {
      tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
      value: huks.HuksKeyAlg.HUKS_ALG_AES
    },
    {
      tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
      value: huks.HuksKeySize.HUKS_AES_KEY_SIZE_256
    },
    {
      tag: huks.HuksTag.HUKS_TAG_PURPOSE,
      value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT | huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_DECRYPT
    },
    {
      tag: huks.HuksTag.HUKS_TAG_BLOCK_MODE,
      value: huks.HuksCipherMode.HUKS_MODE_CBC
    },
    {
      tag: huks.HuksTag.HUKS_TAG_PADDING,
      value: huks.HuksKeyPadding.HUKS_PADDING_NONE
    },
    {
      tag: huks.HuksTag.HUKS_TAG_UNWRAP_ALGORITHM_SUITE,
      value: huks.HuksUnwrapSuite.HUKS_UNWRAP_SUITE_ECDH_AES_256_GCM_NOPADDING
    }
  ];
  let options: huks.HuksOptions = {
    properties: properties
  };
  return options;
};

function huksImportWrappedKey() {
  let genOptions = makeGenerateOptions();
  let importOptions = makeImportOptions();
  TestImportWrappedKeyFunc(
    alias1,
    alias2,
    genOptions,
    importOptions
  );
}
```


<a id="importwrappedkeyitem-1"></a>

## importWrappedKeyItem

```TypeScript
function importWrappedKeyItem(keyAlias: string, wrappingKeyAlias: string, options: HuksOptions): Promise<void>
```

Imports keys in secure mode. This API uses a promise to return the result.

> **NOTE:** 
> 
> Importing SE security level wrapped keys defined in [HuksKeySecurityLevel](arkts-universalkeystore-huks-hukskeysecuritylevel-e.md)
> requires the ohos.permission.ACCESS_SE_KEY permission.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Huks.Extension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keyAlias | string | Yes | Alias of the wrapped key to import. |
| wrappingKeyAlias | string | Yes | Alias of the data used to unwrap the key imported. |
| options | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | Yes | Tags required for the import and the wrapped key to import. The algorithm, key purpose, and key length are mandatory. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed: call the importWrappedKeyItem API, missing Permission: ohos.permission.ACCESS_SE_KEY.<br>**Applicable version:** 26.0.0 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability. 2. The chip does not support the capability. 3. A dependent service feature is not supported. |
| [12000001](../errorcode-huks.md#12000001-feature-not-supported) | algorithm mode is not supported |
| [12000002](../errorcode-huks.md#12000002-missing-key-algorithm-parameter) | algorithm param is missing |
| [12000003](../errorcode-huks.md#12000003-invalid-key-algorithm-parameter) | algorithm param is invalid |
| [12000004](../errorcode-huks.md#12000004-file-error) | operating file failed |
| [12000005](../errorcode-huks.md#12000005-ipc-error) | IPC communication failed |
| [12000006](../errorcode-huks.md#12000006-algorithm-library-operation-failed) | error occurred in crypto engine |
| [12000011](../errorcode-huks.md#12000011-the-entity-does-not-exist) | queried entity does not exist |
| [12000012](../errorcode-huks.md#12000012-external-error) | Device environment or input parameter abnormal |
| [12000013](../errorcode-huks.md#12000013-the-credential-does-not-exist) | queried credential does not exist |
| [12000014](../errorcode-huks.md#12000014-insufficient-memory) | memory is insufficient |
| [12000015](../errorcode-huks.md#12000015-failed-to-invoke-other-system-services) | Failed to obtain the security information via UserIAM |
| [12000017](../errorcode-huks.md#12000017-duplicate-key-alias) | The key with the same alias already exists<br>**Applicable version:** 20 and later |
| [12000018](../errorcode-huks.md#12000018-invalid-input-parameter) | the group id specified by the access group tag is invalid<br>**Applicable version:** 23 and later |
| [12000020](../errorcode-huks.md#12000020-dependent-module-error) | the provider operation failed<br>**Applicable version:** 26.0.0 and later |
| [12000021](../errorcode-huks.md#12000021-ukey-pin-locked) | the UKey PIN is locked<br>**Applicable version:** 26.0.0 and later |
| [12000023](../errorcode-huks.md#12000023-unauthenticated-ukey-pin) | the UKey PIN not authenticated<br>**Applicable version:** 26.0.0 and later |
| [12000024](../errorcode-huks.md#12000024-device-or-resource-busy) | the provider or UKey is busy<br>**Applicable version:** 26.0.0 and later |
| [12000026](../errorcode-huks.md#12000026-secure-element-fault) | the secure element is not available<br>**Applicable version:** 26.0.0 and later |

**Examples**

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';

/* The process is similar if a callback is used, except the following: */
/* The key data imported may be different from the sample code given below. The data structure is described in the preceding comments. */
async function TestImportWrappedFunc(alias: string, wrappingAlias: string, options: huks.HuksOptions) {
  await huks.importWrappedKeyItem(alias, wrappingAlias, options)
    .then(() => {
      console.info(`promise: importWrappedKeyItem success`);
    });
}
```
