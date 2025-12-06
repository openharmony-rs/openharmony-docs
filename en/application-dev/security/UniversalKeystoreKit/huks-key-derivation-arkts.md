# Key Derivation (ArkTS)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

This topic walks you through on how to derive a 256-bit key using HKDF. For details about the scenarios and supported algorithm specifications, see [Supported Algorithms](huks-key-derivation-overview.md#supported-algorithms).

## How to Develop

**Key Generation**

1. Specify the key alias. For details about the naming rules, see [Key Generation Overview and Algorithm Specifications](huks-key-generation-overview.md).

2. Initialize the key property set. You can set **HUKS_TAG_DERIVED_AGREED_KEY_STORAGE_FLAG** (optional) to specify how the key derived from this key is managed.

    - If this tag is set to **HUKS_STORAGE_ONLY_USED_IN_HUKS**, the derived key is managed by HUKS. That is, the derived key is always in a secure environment throughout its lifecycle.

    - If this tag is set to **HUKS_STORAGE_KEY_EXPORT_ALLOWED**, the derived key will be returned to the caller for management. That is, the service side ensures the key security.

    - If this tag is not set, the derived key can be either managed by HUKS or returned to the caller for management. The key protection mode can be set in the subsequent key derivation on the service side.

3. Use [generateKeyItem](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksgeneratekeyitem9) to generate a key. For details, see [Key Generation](huks-key-generation-overview.md).

Alternatively, you can [import a key](huks-key-import-overview.md).

**Key Derivation**

1. Obtain the key alias and set the **HuksOptions** parameter.

    You can set **HUKS_TAG_DERIVED_AGREED_KEY_STORAGE_FLAG** to specify how the derived key is managed.

    | Key Generation| Key Derivation| Specifications|
    | -------- | -------- | -------- |
    | HUKS_STORAGE_ONLY_USED_IN_HUKS | HUKS_STORAGE_ONLY_USED_IN_HUKS | The key is managed by HUKS.|
    | HUKS_STORAGE_KEY_EXPORT_ALLOWED | HUKS_STORAGE_KEY_EXPORT_ALLOWED | The key is returned to the caller for management.|
    | The tag is not set.| HUKS_STORAGE_ONLY_USED_IN_HUKS | The key is managed by HUKS.|
    | The tag is not set.| HUKS_STORAGE_KEY_EXPORT_ALLOWED | The key is returned to the caller for management.|
    | The tag is not set.| The tag is not set.| The key is returned to the caller for management.|

    Note: The tag value set in key derivation should not conflict with the tag value set in key generation. The above table lists only valid settings.


2. Use [initSession](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksinitsession9) to initialize a key session. The session handle is returned after the initialization.

3. Use [updateSession](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksupdatesession9) to process data.

4. Use [finishSession](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksfinishsession9) to derive a key.

**Key Deletion**

Use [deleteKeyItem](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksdeletekeyitem9) to delete the key that is not required. For details, see [Deleting a Key](huks-delete-key-arkts.md).

## Development Cases

### HKDF
```ts
/*
 * Derive an HKDF key using promise-based APIs.
 */
import { huks } from '@kit.UniversalKeystoreKit';
import { BusinessError } from "@kit.BasicServicesKit";

function StringToUint8Array(str: string) {
  let arr: number[] = new Array();
  for (let i = 0, j = str.length; i < j; ++i) {
    arr.push(str.charCodeAt(i));
  }
  return new Uint8Array(arr);
}

function Uint8ArrayToString(fileData: Uint8Array) {
  let dataString = '';
  for (let i = 0; i < fileData.length; i++) {
    dataString += String.fromCharCode(fileData[i]);
  }
  return dataString;
}

/*
 * Set the key alias and encapsulate the key property set.
 */
let srcKeyAlias = "hkdf_Key";
let deriveHkdfInData = "deriveHkdfTestIndata";
let handle: number;
let HuksKeyDeriveKeySize = 32;
/* Set the parameter set used for key generation. */
let properties: Array<huks.HuksParam> = [{
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_AES,
  }, {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_DERIVE,
  }, {
    tag: huks.HuksTag.HUKS_TAG_DIGEST,
    value: huks.HuksKeyDigest.HUKS_DIGEST_SHA256,
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_AES_KEY_SIZE_256,
  }, {
    tag: huks.HuksTag.HUKS_TAG_DERIVED_AGREED_KEY_STORAGE_FLAG,
    value: huks.HuksKeyStorageType.HUKS_STORAGE_ONLY_USED_IN_HUKS,
  }
];

let huksOptions: huks.HuksOptions = {
  properties: properties,
  inData: new Uint8Array(new Array())
}
/* Set the parameter set used for init(). */
let initProperties: Array<huks.HuksParam> = [{
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_HKDF,
  }, {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_DERIVE,
  }, {
    tag: huks.HuksTag.HUKS_TAG_DIGEST,
    value: huks.HuksKeyDigest.HUKS_DIGEST_SHA256,
  }, {
    tag: huks.HuksTag.HUKS_TAG_DERIVE_KEY_SIZE,
    value: HuksKeyDeriveKeySize,
  }
];

let initOptions: huks.HuksOptions = {
  properties: initProperties,
  inData: new Uint8Array(new Array())
}
/* Set the parameter set used for finish(). */
let finishProperties: Array<huks.HuksParam> = [{
    tag: huks.HuksTag.HUKS_TAG_DERIVED_AGREED_KEY_STORAGE_FLAG,
    value: huks.HuksKeyStorageType.HUKS_STORAGE_ONLY_USED_IN_HUKS,
  }, {
    tag: huks.HuksTag.HUKS_TAG_IS_KEY_ALIAS,
    value: true,
  }, {
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_AES,
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_AES_KEY_SIZE_256,
  }, {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value:
    huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT |
    huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_DECRYPT,
  }, {
    tag: huks.HuksTag.HUKS_TAG_DIGEST,
    value: huks.HuksKeyDigest.HUKS_DIGEST_NONE,
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_ALIAS,
    value: StringToUint8Array(srcKeyAlias),
  }, {
    tag: huks.HuksTag.HUKS_TAG_PADDING,
    value: huks.HuksKeyPadding.HUKS_PADDING_NONE,
  }, {
    tag: huks.HuksTag.HUKS_TAG_BLOCK_MODE,
    value: huks.HuksCipherMode.HUKS_MODE_ECB,
  }
];
let finishOptions: huks.HuksOptions = {
  properties: finishProperties,
  inData: new Uint8Array(new Array())
}

async function generateKeyItem(keyAlias: string, huksOptions: huks.HuksOptions) {
  console.info(`promise: enter generateKeyItem`);
  try {
    await huks.generateKeyItem(keyAlias, huksOptions)
      .then(() => {
        console.info(`promise: generateKeyItem success`);
      }).catch((error: BusinessError) => {
        console.error(`promise: generateKeyItem failed, errCode : ${error.code}, errMsg : ${error.message}`);
      })
  } catch (error) {
    console.error(`promise: generateKeyItem input arg invalid`);
  }
}

async function initSession(keyAlias: string, huksOptions: huks.HuksOptions) {
  console.info(`promise: enter initSession`);
  try {
    await huks.initSession(keyAlias, huksOptions)
      .then((data) => {
        handle = data.handle;
        console.info(`promise: initSession success`);
      }).catch((error: BusinessError) => {
        console.error(`promise: initSession failed, errCode : ${error.code}, errMsg : ${error.message}`);
      })
  } catch (error) {
    console.error(`promise: initSession input arg invalid`);
  }
}

async function updateSession(handle: number, huksOptions: huks.HuksOptions) {
  console.info(`promise: enter updateSession`);
  try {
    await huks.updateSession(handle, huksOptions)
      .then((data) => {
        let outData = data.outData as Uint8Array;
        console.info(`promise: updateSession success, data = ${Uint8ArrayToString(outData)}`);
      }).catch((error: BusinessError) => {
        console.error(`promise: updateSession failed, errCode : ${error.code}, errMsg : ${error.message}`);
      })
  } catch (error) {
    console.error(`promise: updateSession input arg invalid`);
  }
}

async function finishSession(handle: number, huksOptions: huks.HuksOptions) {
  console.info(`promise: enter finishSession`);
  try {
    await huks.finishSession(handle, huksOptions)
      .then((data) => {
        let outData = data.outData as Uint8Array;
        console.info(`promise: finishSession success, data = ${Uint8ArrayToString(outData)}`);
      }).catch((error: BusinessError) => {
        console.error(`promise: finishSession failed, errCode : ${error.code}, errMsg : ${error.message}`);
      })
  } catch (error) {
    console.error(`promise: finishSession input arg invalid`);
  }
}

async function deleteKeyItem(keyAlias: string, huksOptions: huks.HuksOptions) {
  console.info(`promise: enter deleteKeyItem`);
  try {
    await huks.deleteKeyItem(keyAlias, huksOptions)
      .then(() => {
        console.info(`promise: deleteKeyItem success`);
      }).catch((error: BusinessError) => {
        console.error(`promise: deleteKeyItem failed, errCode : ${error.code}, errMsg : ${error.message}`);
      })
  } catch (error) {
    console.error(`promise: deleteKeyItem input arg invalid`);
  }
}

async function testDerive() {
  /* Generate a key. */
  await generateKeyItem(srcKeyAlias, huksOptions);
  /* Perform key derivation. */
  await initSession(srcKeyAlias, initOptions);
  initOptions.inData = StringToUint8Array(deriveHkdfInData);
  await updateSession(handle, initOptions);
  await finishSession(handle, finishOptions);
  await deleteKeyItem(srcKeyAlias, huksOptions);
}
```
### PBKDF2

```ts
/*
 * Derive a PBKDF2 key using promise-based APIs.
 */
import { huks } from '@kit.UniversalKeystoreKit';
import { BusinessError } from "@kit.BasicServicesKit";

function StringToUint8Array(str: string) {
  let arr: number[] = new Array();
  for (let i = 0, j = str.length; i < j; ++i) {
    arr.push(str.charCodeAt(i));
  }
  return new Uint8Array(arr);
}

function Uint8ArrayToString(fileData: Uint8Array) {
  let dataString = '';
  for (let i = 0; i < fileData.length; i++) {
    dataString += String.fromCharCode(fileData[i]);
  }
  return dataString;
}

/*
 * Set the key alias and encapsulate the key property set.
 */
let srcKeyAlias = "pbkdf2_Key";
let salt = "mySalt";
let iterationCount = 10000;
let derivedKeySize = 32;
let handle: number;
let finishOutData: Uint8Array;

/* Set the parameter set used for key generation. */
let properties: Array<huks.HuksParam> = [{
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_AES,
  }, {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_DERIVE,
  }, {
    tag: huks.HuksTag.HUKS_TAG_DIGEST,
    value: huks.HuksKeyDigest.HUKS_DIGEST_SHA256,
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_AES_KEY_SIZE_256,
  }, {
    tag: huks.HuksTag.HUKS_TAG_DERIVED_AGREED_KEY_STORAGE_FLAG,
    value: huks.HuksKeyStorageType.HUKS_STORAGE_ONLY_USED_IN_HUKS,
  }
];

let huksOptions: huks.HuksOptions = {
  properties: properties,
  inData: new Uint8Array(new Array())
}

/* Set the parameter set used for init(). */
let initProperties: Array<huks.HuksParam> = [{
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_PBKDF2,
  }, {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_DERIVE,
  }, {
    tag: huks.HuksTag.HUKS_TAG_DIGEST,
    value: huks.HuksKeyDigest.HUKS_DIGEST_SHA256,
  }, {
    tag: huks.HuksTag.HUKS_TAG_DERIVE_KEY_SIZE,
    value: derivedKeySize,
  }, {
    tag: huks.HuksTag.HUKS_TAG_ITERATION,
    value: iterationCount,
  }, {
    tag: huks.HuksTag.HUKS_TAG_SALT,
    value: StringToUint8Array(salt),
  }
];

let initOptions: huks.HuksOptions = {
  properties: initProperties,
  inData: new Uint8Array(new Array())
}

/* Set the parameter set used for finish(). */
let finishProperties: Array<huks.HuksParam> = [{
    tag: huks.HuksTag.HUKS_TAG_DERIVED_AGREED_KEY_STORAGE_FLAG,
    value: huks.HuksKeyStorageType.HUKS_STORAGE_ONLY_USED_IN_HUKS,
  }, {
    tag: huks.HuksTag.HUKS_TAG_IS_KEY_ALIAS,
    value: true,
  }, {
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_AES,
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_AES_KEY_SIZE_256,
  }, {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT | huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_DECRYPT,
  }, {
    tag: huks.HuksTag.HUKS_TAG_DIGEST,
    value: huks.HuksKeyDigest.HUKS_DIGEST_NONE,
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_ALIAS,
    value: StringToUint8Array(srcKeyAlias),
  }, {
    tag: huks.HuksTag.HUKS_TAG_PADDING,
    value: huks.HuksKeyPadding.HUKS_PADDING_NONE,
  }, {
    tag: huks.HuksTag.HUKS_TAG_BLOCK_MODE,
    value: huks.HuksCipherMode.HUKS_MODE_ECB,
  }
];

let finishOptions: huks.HuksOptions = {
  properties: finishProperties,
  inData: new Uint8Array(new Array())
}

async function generateKeyItem(keyAlias: string, huksOptions: huks.HuksOptions) {
  console.info(`promise: enter generateKeyItem`);
  try {
    await huks.generateKeyItem(keyAlias, huksOptions)
      .then(() => {
        console.info(`promise: generateKeyItem success`);
      }).catch((error: BusinessError) => {
        console.error(`promise: generateKeyItem failed, errCode : ${error.code}, errMsg : ${error.message}`);
      })
  } catch (error) {
    console.error(`promise: generateKeyItem input arg invalid`);
  }
}

async function initSession(keyAlias: string, huksOptions: huks.HuksOptions) {
  console.info(`promise: enter initSession`);
  try {
    await huks.initSession(keyAlias, huksOptions)
      .then((data) => {
        handle = data.handle;
        console.info(`promise: initSession success`);
      }).catch((error: BusinessError) => {
        console.error(`promise: initSession failed, errCode : ${error.code}, errMsg : ${error.message}`);
      })
  } catch (error) {
    console.error(`promise: initSession input arg invalid`);
  }
}

async function updateSession(handle: number, huksOptions: huks.HuksOptions) {
  console.info(`promise: enter updateSession`);
  try {
    await huks.updateSession(handle, huksOptions)
      .then((data) => {
        let outData = data.outData as Uint8Array;
        console.info(`promise: updateSession success, data = ${Uint8ArrayToString(outData)}`);
      }).catch((error: BusinessError) => {
        console.error(`promise: updateSession failed, errCode : ${error.code}, errMsg : ${error.message}`);
      })
  } catch (error) {
    console.error(`promise: updateSession input arg invalid`);
  }
}

async function finishSession(handle: number, huksOptions: huks.HuksOptions) {
  console.info(`promise: enter finishSession`);
  try {
    await huks.finishSession(handle, huksOptions)
      .then((data) => {
        let outData = data.outData as Uint8Array;
        console.info(`promise: finishSession success, data = ${Uint8ArrayToString(outData)}`);
      }).catch((error: BusinessError) => {
        console.error(`promise: finishSession failed, errCode : ${error.code}, errMsg : ${error.message}`);
      })
  } catch (error) {
    console.error(`promise: finishSession input arg invalid`);
  }
}

async function deleteKeyItem(keyAlias: string, huksOptions: huks.HuksOptions) {
  console.info(`promise: enter deleteKeyItem`);
  try {
    await huks.deleteKeyItem(keyAlias, huksOptions)
      .then(() => {
        console.info(`promise: deleteKeyItem success`);
      }).catch((error: BusinessError) => {
        console.error(`promise: deleteKeyItem failed, errCode : ${error.code}, errMsg : ${error.message}`);
      })
  } catch (error) {
    console.error(`promise: deleteKeyItem input arg invalid`);
  }
}
async function testDerive() {
  /* Generate a key. */
  await generateKeyItem(srcKeyAlias, huksOptions);
  /* Perform key derivation. */
  await initSession(srcKeyAlias, initOptions);
  await updateSession(handle, initOptions);
  await finishSession(handle, finishOptions);
  await deleteKeyItem(srcKeyAlias, huksOptions);
}
```
