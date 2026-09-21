# importKeyItem

## Modules to Import

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
```

## importKeyItem

```TypeScript
function importKeyItem(keyAlias: string, options: HuksOptions, callback: AsyncCallback<void>): void
```

Imports a key in plaintext. This API uses an asynchronous callback to return the result.

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** 
- API version 12 and later: SystemCapability.Security.Huks.Core
- API versions 9 to 11: SystemCapability.Security.Huks.Extension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keyAlias | string | Yes | Alias of the key. The value can contain up to 128 bytes and should not include sensitive data such as personal information. |
| options | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | Yes | Tags required for the import and key to import. The algorithm, key purpose, and key length are mandatory. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability. 2. The chip does not support the capability. 3. A dependent service feature is not supported. |
| [12000001](../errorcode-huks.md#12000001-feature-not-supported) | algorithm mode is not supported |
| [12000002](../errorcode-huks.md#12000002-missing-key-algorithm-parameter) | algorithm param is missing |
| [12000003](../errorcode-huks.md#12000003-invalid-key-algorithm-parameter) | algorithm param is invalid |
| [12000004](../errorcode-huks.md#12000004-file-error) | operating file failed |
| [12000005](../errorcode-huks.md#12000005-ipc-error) | IPC communication failed |
| [12000006](../errorcode-huks.md#12000006-algorithm-library-operation-failed) | error occurred in crypto engine |
| [12000011](../errorcode-huks.md#12000011-the-entity-does-not-exist) | queried entity does not exist<br>**Applicable version:** 9 - 19 |
| [12000012](../errorcode-huks.md#12000012-external-error) | Device environment or input parameter abnormal |
| [12000013](../errorcode-huks.md#12000013-the-credential-does-not-exist) | queried credential does not exist |
| [12000014](../errorcode-huks.md#12000014-insufficient-memory) | memory is insufficient |
| [12000015](../errorcode-huks.md#12000015-failed-to-invoke-other-system-services) | Failed to obtain the security information via UserIAM |
| [12000017](../errorcode-huks.md#12000017-duplicate-key-alias) | The key with the same alias already exists<br>**Applicable version:** 20 and later |
| [12000018](../errorcode-huks.md#12000018-invalid-input-parameter) | the group id specified by the access group tag is invalid<br>**Applicable version:** 23 and later |

**Examples**

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';

/* Import a 256-bit AES key. */
let plainTextSize32 = makeRandomArr(32);

function makeRandomArr(size: number) {
  let arr = new Uint8Array(size);
  for (let i = 0; i < size; i++) {
    arr[i] = Math.floor(Math.random() * 10);
  }
  return arr;
};
let keyAlias = 'keyAlias';
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
    value:
    huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT | huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_DECRYPT
  },
  {
    tag: huks.HuksTag.HUKS_TAG_PADDING,
    value: huks.HuksKeyPadding.HUKS_PADDING_PKCS7
  },
  {
    tag: huks.HuksTag.HUKS_TAG_BLOCK_MODE,
    value: huks.HuksCipherMode.HUKS_MODE_ECB
  }
];
let options: huks.HuksOptions = {
  properties: properties,
  inData: plainTextSize32
};
huks.importKeyItem(keyAlias, options, (error) => {
  if (error) {
    console.error(`callback: importKeyItem failed`);
  } else {
    console.info(`callback: importKeyItem success`);
  }
});
```


<a id="importkeyitem-1"></a>

## importKeyItem

```TypeScript
function importKeyItem(keyAlias: string, options: HuksOptions): Promise<void>
```

Imports a key in plaintext. This API uses a promise to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Security.Huks.Extension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keyAlias | string | Yes | Alias of the key. The value can contain up to 128 bytes and should not include sensitive data such as personal information. |
| options | [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | Yes | Tags required for the import and key to import. The algorithm, key purpose, and key length are mandatory. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability. 2. The chip does not support the capability. 3. A dependent service feature is not supported. |
| [12000001](../errorcode-huks.md#12000001-feature-not-supported) | algorithm mode is not supported |
| [12000002](../errorcode-huks.md#12000002-missing-key-algorithm-parameter) | algorithm param is missing |
| [12000003](../errorcode-huks.md#12000003-invalid-key-algorithm-parameter) | algorithm param is invalid |
| [12000004](../errorcode-huks.md#12000004-file-error) | operating file failed |
| [12000005](../errorcode-huks.md#12000005-ipc-error) | IPC communication failed |
| [12000006](../errorcode-huks.md#12000006-algorithm-library-operation-failed) | error occurred in crypto engine |
| [12000011](../errorcode-huks.md#12000011-the-entity-does-not-exist) | queried entity does not exist<br>**Applicable version:** 9 - 19 |
| [12000012](../errorcode-huks.md#12000012-external-error) | Device environment or input parameter abnormal |
| [12000013](../errorcode-huks.md#12000013-the-credential-does-not-exist) | queried credential does not exist |
| [12000014](../errorcode-huks.md#12000014-insufficient-memory) | memory is insufficient |
| [12000015](../errorcode-huks.md#12000015-failed-to-invoke-other-system-services) | Failed to obtain the security information via UserIAM |
| [12000017](../errorcode-huks.md#12000017-duplicate-key-alias) | The key with the same alias already exists<br>**Applicable version:** 20 and later |
| [12000018](../errorcode-huks.md#12000018-invalid-input-parameter) | the group id specified by the access group tag is invalid<br>**Applicable version:** 23 and later |

**Examples**

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';

/* Import an AES key of 256 bits. */
function makeRandomArr(size: number) {
  let arr = new Uint8Array(size);
  for (let i = 0; i < size; i++) {
    arr[i] = Math.floor(Math.random() * 10);
  }
  return arr;
};

/* Step 1 Generate a key. */
let plainTextSize32 = makeRandomArr(32);
let keyAlias = 'keyAlias';
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
    tag: huks.HuksTag.HUKS_TAG_PADDING,
    value: huks.HuksKeyPadding.HUKS_PADDING_PKCS7
  },
  {
    tag: huks.HuksTag.HUKS_TAG_BLOCK_MODE,
    value: huks.HuksCipherMode.HUKS_MODE_ECB
  }
];
let huksOptions: huks.HuksOptions = {
  properties: properties,
  inData: plainTextSize32
};
/* Step 2: Import the key. */
huks.importKeyItem(keyAlias, huksOptions)
  .then(() => {
    console.info(`promise: importKeyItem success`);
  });
```
