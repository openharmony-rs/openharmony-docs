# Group Key (ArkTS)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

From API version 23, HUKS supports the group key function. For details about the HUKS key operations supported by the group key function, see [Group Key Overview](huks-group-key-overview.md). This guide describes [Encryption and Decryption Using AES/CBC/PKCS7](#encryption-and-decryption-using-aescbcpkcs7), [Asymmetric Key Negotiation Using X25519](#asymmetric-key-agreement-using-x25519), and [Key Derivation Using PBKDF2](#key-derivation-using-pbkdf2) as examples to show how to use group keys.

**Configuration file**

Before using a group key, you need to configure the group information in the **app.json5** file. For details, see the configuration method of the **assetAccessGroups** field in [Configuration File Example](../../quick-start/app-configuration-file.md#configuration-file-example).

## Encryption and Decryption Using AES/CBC/PKCS7

### How to Develop

**Key generation**

1. Set a key alias. For details about the naming rules, see [Key Generation Overview and Algorithm Specifications](huks-key-generation-overview.md).

2. Initialize the key property set. Add the group key tag [HUKS_TAG_KEY_ACCESS_GROUP](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukstag). [HUKS_TAG_KEY_OVERRIDE](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukstag) is recommended to prevent the key from being overwritten.

3. Call [generateKeyItem](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksgeneratekeyitem9) to generate a key. For details, see [Key Generation Overview and Algorithm Specifications](huks-key-generation-overview.md).

Alternatively, you can [import a key](huks-key-import-overview.md).

**Encryption**

1. Set a key alias.

2. Specify the data to be encrypted.

3. Set encryption [algorithm parameters](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksparam). Add the group key tag [HUKS_TAG_KEY_ACCESS_GROUP](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukstag).

4. Call [initSession](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksinitsession9) to initialize a key session and obtain the session handle.

5. Call [finishSession](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksfinishsession9) to finish the key session and obtain the ciphertext.

**Decryption**

1. Set a key alias.

2. Specify the ciphertext to be decrypted.

3. Set decryption [algorithm parameters](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksparam). Add the group key tag [HUKS_TAG_KEY_ACCESS_GROUP](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukstag).

4. Call [initSession](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksinitsession9) to initialize a key session and obtain the session handle.

5. Call [finishSession](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksfinishsession9) to finish the key session and obtain the data decrypted.

**Key deletion**

1. Set a key alias.

2. Set key deletion [algorithm parameters](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksparam). Add the group key tag [HUKS_TAG_KEY_ACCESS_GROUP](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukstag).

3. Call [deleteKeyItem](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksdeletekeyitem9) to delete the key. For details, see [Deleting a Key (ArkTS)](huks-delete-key-arkts.md).

### Development Cases

```ts
/*
 * The following uses AES/CBC/PKCS7 with promise-based APIs.
 */
import { huks } from '@kit.UniversalKeystoreKit';
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { BusinessError } from "@kit.BasicServicesKit";

let aesKeyAlias = 'groupKeyTestAesKeyAlias';
let handle: number;
let plainText = '123456';
let IV = cryptoFramework.createRandom().generateRandomSync(12).data;
let cipherData: Uint8Array;
/*
 * Add the group information to the assetAccessGroups field in app.json5.
 */
let group = 'ohos.test.groupKey';

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

function GetAesGenerateProperties() {
  let properties: Array<huks.HuksParam> = [{
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_AES
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_AES_KEY_SIZE_128
  }, {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT | huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_DECRYPT
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_ACCESS_GROUP,
    value: StringToUint8Array(group)
  }];
  return properties;
}

function GetAesEncryptProperties() {
  let properties: Array<huks.HuksParam> = [{
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_AES
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_AES_KEY_SIZE_128
  }, {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT
  }, {
    tag: huks.HuksTag.HUKS_TAG_PADDING,
    value: huks.HuksKeyPadding.HUKS_PADDING_PKCS7
  }, {
    tag: huks.HuksTag.HUKS_TAG_BLOCK_MODE,
    value: huks.HuksCipherMode.HUKS_MODE_CBC
  }, {
    tag: huks.HuksTag.HUKS_TAG_IV,
    value: IV
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_ACCESS_GROUP,
    value: StringToUint8Array(group)
  }];
  return properties;
}

function GetAesDecryptProperties() {
  let properties: Array<huks.HuksParam> = [{
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_AES
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_AES_KEY_SIZE_128
  }, {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_DECRYPT
  }, {
    tag: huks.HuksTag.HUKS_TAG_PADDING,
    value: huks.HuksKeyPadding.HUKS_PADDING_PKCS7
  }, {
    tag: huks.HuksTag.HUKS_TAG_BLOCK_MODE,
    value: huks.HuksCipherMode.HUKS_MODE_CBC
  }, {
    tag: huks.HuksTag.HUKS_TAG_IV,
    value: IV
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_ACCESS_GROUP,
    value: StringToUint8Array(group)
  }];
  return properties;
}

async function GenerateAesKey() {
  /*
   * Simulate the key generation scenario.
   * 1. Set a key alias.
   */
  /*
   * 2. Obtain the algorithm parameters for key generation.
   */
  let genProperties = GetAesGenerateProperties();
  let options: huks.HuksOptions = {
    properties: genProperties
  }
  /*
   * 3. Call generateKeyItem.
   */
  await huks.generateKeyItem(aesKeyAlias, options)
    .then(() => {
      console.info(`promise: generate AES Key success`);
    }).catch((error: BusinessError) => {
      console.error(`promise: generate AES Key failed, errCode: ${error.code}, errMsg: ${error.message}`);
    })
}

async function EncryptData() {
  /*
   * Simulate the encryption scenario.
   * 1. Obtain the key alias.
   */
  /*
   * 2. Obtain the data to be encrypted.
   */
  /*
   * 3. Obtain the algorithm parameters for encryption.
   */
  let encryptProperties = GetAesEncryptProperties();
  let options: huks.HuksOptions = {
    properties: encryptProperties,
    inData: StringToUint8Array(plainText)
  }
  /*
   * 4. Call initSession to obtain a session handle.
   */
  await huks.initSession(aesKeyAlias, options)
    .then((data) => {
      handle = data.handle;
    }).catch((error: BusinessError) => {
      console.error(`promise: init EncryptData failed, errCode: ${error.code}, errMsg: ${error.message}`);
    })
  /*
   * 5. Call finishSession to obtain the ciphertext.
   */
  await huks.finishSession(handle, options)
    .then((data) => {
      console.info(`promise: encrypt data success, data is ` + Uint8ArrayToString(data.outData as Uint8Array));
      cipherData = data.outData as Uint8Array;
    }).catch((error: BusinessError) => {
      console.error(`promise: encrypt data failed, errCode: ${error.code}, errMsg: ${error.message}`);
    })
}

async function DecryptData() {
  /*
   * Simulate the decryption scenario.
   * 1. Obtain the key alias.
   */
  /*
   * 2. Obtain the ciphertext to be decrypted.
   */
  /*
   * 3. Obtain the algorithm parameters for decryption.
   */
  let decryptOptions = GetAesDecryptProperties()
  let options: huks.HuksOptions = {
    properties: decryptOptions,
    inData: cipherData
  }
  /*
   * 4. Call initSession to obtain a session handle.
   */
  await huks.initSession(aesKeyAlias, options)
    .then((data) => {
      handle = data.handle;
    }).catch((error: BusinessError) => {
      console.error(`promise: init DecryptData failed, errCode: ${error.code}, errMsg: ${error.message}`);
    })
  /*
   * 5. Call finishSession to obtain the decrypted data.
   */
  await huks.finishSession(handle, options)
    .then((data) => {
      console.info(`promise: decrypt data success, data is ` + Uint8ArrayToString(data.outData as Uint8Array));
    }).catch((error: BusinessError) => {
      console.error(`promise: decrypt data failed, errCode: ${error.code}, errMsg: ${error.message}`);
    })
}

async function DeleteKey() {
  /*
   * Simulate the key deletion scenario.
   * 1. Obtain the key alias.
   */
  let deleteProperties: Array<huks.HuksParam> = [
    {
      tag: huks.HuksTag.HUKS_TAG_KEY_ACCESS_GROUP,
      value: StringToUint8Array(group)
    }
  ]
  let deleteOptions: huks.HuksOptions = {
    properties: deleteProperties
  }
  /*
   * 2. Call deleteKeyItem to delete the key.
   */
  await huks.deleteKeyItem(aesKeyAlias, deleteOptions)
    .then(() => {
      console.info(`promise: delete data success`);
    }).catch((error: BusinessError) => {
      console.error(`promise: delete data failed, errCode: ${error.code}, errMsg: ${error.message}`);
    })
}

async function TestGroupKeyEncryptDecrypt() {
  await GenerateAesKey();
  await EncryptData();
  await DecryptData();
  await DeleteKey();
}
```

## Asymmetric Key Agreement Using X25519

### How to Develop

**Key generation**

Generate an asymmetric key for device A and device B each. For details, see [Key Generation Overview and Algorithm Specifications](huks-key-generation-overview.md) or [Key Import Overview and Algorithm Specifications](huks-key-import-overview.md).

When generating a key, specify [HUKS_TAG_KEY_ACCESS_GROUP](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukstag) to generate a group key.

**Key export**

Export the public key of the asymmetric key pair of device A and device B. For details, see [Exporting a Key (ArkTS)](huks-export-key-arkts.md).

When exporting a key, specify [HUKS_TAG_KEY_ACCESS_GROUP](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukstag) to export a group key.

**Key agreement**

Perform key agreement using the public key of the peer device and private key of the local device (that is, public key of device B and private key of device A for device A, and public key of device A and private key of device B for device B) to produce a shared key.

When performing key agreement, specify [HUKS_TAG_KEY_ACCESS_GROUP](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukstag) to produce a group key.

**Key deletion**

Delete the keys from device A and device B when the keys are not required. For details, see [Deleting a Key (ArkTS)](huks-delete-key-arkts.md).

When deleting a key, specify [HUKS_TAG_KEY_ACCESS_GROUP](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukstag) to delete the group key.

### Development Cases

```ts
/*
 * Agree on an X25519 key using promise-based APIs.
 * Produce a group key using group key agreement.
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
 * Set a key alias and encapsulate the key property set.
 */
let srcKeyAliasFirst = "AgreeX25519KeyFirstAlias";
let srcKeyAliasSecond = "AgreeX25519KeySecondAlias";
let agreeX25519InData = 'AgreeX25519TestIndata';
let finishOutData: Uint8Array;
let handle: number;
let exportKey: Uint8Array;
let exportKeyFirst: Uint8Array;
let exportKeySecond: Uint8Array;
/*
 * Add the group information to the assetAccessGroups field in app.json5.
 */
let group = 'ohos.test.groupKey';
/* Set the parameter set for key generation. */
let properties: Array<huks.HuksParam> = [{
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_X25519,
  }, {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_AGREE,
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_CURVE25519_KEY_SIZE_256,
  }, {
    tag: huks.HuksTag.HUKS_TAG_DIGEST,
    value: huks.HuksKeyDigest.HUKS_DIGEST_NONE,
  }, {
    tag: huks.HuksTag.HUKS_TAG_PADDING,
    value: huks.HuksKeyPadding.HUKS_PADDING_NONE,
  }, {
    tag: huks.HuksTag.HUKS_TAG_BLOCK_MODE,
    value: huks.HuksCipherMode.HUKS_MODE_CBC,
  }, {
    tag: huks.HuksTag.HUKS_TAG_DERIVED_AGREED_KEY_STORAGE_FLAG,
    value: huks.HuksKeyStorageType.HUKS_STORAGE_ONLY_USED_IN_HUKS,
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_ACCESS_GROUP,
    value: StringToUint8Array(group)
  }
];
let HuksOptions: huks.HuksOptions = {
  properties: properties,
  inData: new Uint8Array(new Array())
}
const finishProperties: Array<huks.HuksParam> = [{
    tag: huks.HuksTag.HUKS_TAG_DERIVED_AGREED_KEY_STORAGE_FLAG,
    value: huks.HuksKeyStorageType.HUKS_STORAGE_ONLY_USED_IN_HUKS,
  }, {
    tag: huks.HuksTag.HUKS_TAG_IS_KEY_ALIAS,
    value: true
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
    tag: huks.HuksTag.HUKS_TAG_PADDING,
    value: huks.HuksKeyPadding.HUKS_PADDING_NONE,
  }, {
    tag: huks.HuksTag.HUKS_TAG_BLOCK_MODE,
    value: huks.HuksCipherMode.HUKS_MODE_ECB,
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_ACCESS_GROUP,
    value: StringToUint8Array(group)
  }
];
/* Set the parameter set for the first key agreement. */
let finishOptionsFirst: huks.HuksOptions = {
  properties: [
    ...finishProperties, {
    tag: huks.HuksTag.HUKS_TAG_KEY_ALIAS,
    value: StringToUint8Array(srcKeyAliasFirst + 'final'),
  }],
  inData: StringToUint8Array(agreeX25519InData)
}
/* Set the parameter set for the second key agreement. */
let finishOptionsSecond: huks.HuksOptions = {
  properties: [
    ...finishProperties, {
    tag: huks.HuksTag.HUKS_TAG_KEY_ALIAS,
    value: StringToUint8Array(srcKeyAliasSecond + 'final'),
  }],
  inData: StringToUint8Array(agreeX25519InData)
}

/* Generate a key. */
async function generateKeyItem(keyAlias: string, huksOptions: huks.HuksOptions) {
  console.info("promise: enter generateKeyItem");
  try {
    await huks.generateKeyItem(keyAlias, huksOptions)
      .then(() => {
        console.info(`promise: generateKeyItem success`);
      }).catch((error: BusinessError) => {
        console.error(`promise: generateKeyItem failed, errCode: ${error.code}, errMsg: ${error.message}`);
      })
  } catch (error) {
    console.error(`promise: generateKeyItem input arg invalid`);
  }
}

/* Initializes a key session. This function returns a session handle (mandatory) and a challenge value (optional). */
async function initSession(keyAlias: string, huksOptions: huks.HuksOptions) {
  console.info("promise: enter initSession");
  try {
    await huks.initSession(keyAlias, huksOptions)
      .then((data) => {
        handle = data.handle;
        console.info(`promise: initSession success`);
      }).catch((error: BusinessError) => {
        console.error(`promise: initSession failed, errCode: ${error.code}, errMsg: ${error.message}`);
      })
  } catch (error) {
    console.error(`promise: initSession input arg invalid`);
  }
}

/* Call updateSession multiple times to process data by segment and output the processed data. */
async function updateSession(handle: number, huksOptions: huks.HuksOptions) {
  console.info("promise: enter updateSession");
  try {
    await huks.updateSession(handle, huksOptions)
      .then((data) => {
        console.info(`promise: updateSession success, data is ` + Uint8ArrayToString(data.outData as Uint8Array));
      }).catch((error: BusinessError) => {
        console.error(`promise: updateSession failed, errCode: ${error.code}, errMsg: ${error.message}`);
      })
  } catch (error) {
    console.error(`promise: updateSession input arg invalid`);
  }
}

/* Finish the key session to output the shared key. */
async function finishSession(handle: number, huksOptions: huks.HuksOptions) {
  console.info("promise: enter finishSession");
  try {
    await huks.finishSession(handle, huksOptions)
      .then((data) => {
        finishOutData = data.outData as Uint8Array;
        console.info(`promise: finishSession success, data is ` + Uint8ArrayToString(data.outData as Uint8Array));
      }).catch((error: BusinessError) => {
        console.error(`promise: finishSession failed, errCode: ${error.code}, errMsg: ${error.message}`);
      })
  } catch (error) {
    console.error(`promise: finishSession input arg invalid`);
  }
}

/* Export the key. */
async function exportKeyItem(keyAlias: string, huksOptions: huks.HuksOptions) {
  console.info("promise: enter exportKeyItem");
  try {
    await huks.exportKeyItem(keyAlias, huksOptions)
      .then((data) => {
        exportKey = data.outData as Uint8Array;
        console.info(`promise: exportKey success, data is ` + Uint8ArrayToString(data.outData as Uint8Array));
      }).catch((error: BusinessError) => {
        console.error(`promise: exportKeyItem failed, errCode: ${error.code}, errMsg: ${error.message}`);
      })
  } catch (error) {
    console.error(`promise: exportKeyItem input arg invalid`);
  }
}

/* Delete the key. */
async function deleteKeyItem(keyAlias: string, huksOptions: huks.HuksOptions) {
  console.info("promise: enter deleteKeyItem");
  try {
    await huks.deleteKeyItem(keyAlias, huksOptions)
      .then(() => {
        console.info(`promise: deleteKeyItem success`);
      }).catch((error: BusinessError) => {
        console.error(`promise: deleteKeyItem failed, errCode: ${error.code}, errMsg: ${error.message}`);
      })
  } catch (error) {
    console.error(`promise: deleteKeyItem input arg invalid`);
  }
}

async function testAgree() {
  /* 1. Set the key alias to srcKeyAliasFirst for device A and srcKeyAliasSecond for device B, and configure the parameter set for generating a key. */
  /* 2. Generate a key for device A. */
  await generateKeyItem(srcKeyAliasFirst, HuksOptions);
  /* 3. Generate a key for device B. */
  await generateKeyItem(srcKeyAliasSecond, HuksOptions);
  /* 4. Export the public keys of the asymmetric keys of device A and device B. */
  await exportKeyItem(srcKeyAliasFirst, HuksOptions);
  exportKeyFirst = exportKey;
  await exportKeyItem(srcKeyAliasSecond, HuksOptions);
  exportKeySecond = exportKey;
  /* 5. Perform key agreement (Init-Update-Finish) for device A. */
  await initSession(srcKeyAliasFirst, HuksOptions);
  HuksOptions.inData = exportKeySecond;
  await updateSession(handle, HuksOptions);
  await finishSession(handle, finishOptionsFirst);
  /* 6. Perform key agreement (Init-Update-Finish) for device B. */
  await initSession(srcKeyAliasSecond, HuksOptions);
  HuksOptions.inData = exportKeyFirst;
  await updateSession(handle, HuksOptions);
  await finishSession(handle, finishOptionsSecond);
  /* 7. Delete the keys from device A and device B. */
  await deleteKeyItem(srcKeyAliasFirst, HuksOptions);
  await deleteKeyItem(srcKeyAliasSecond, HuksOptions);
}
```

## Key Derivation Using PBKDF2

### How to Develop

**Key generation**

1. Set a key alias. For details about the naming rules, see [Key Generation Overview and Algorithm Specifications](huks-key-generation-overview.md).

2. When generating a key, specify [HUKS_TAG_KEY_ACCESS_GROUP](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukstag) to generate a group key.

3. Call [generateKeyItem](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksgeneratekeyitem9) to generate a key. For details, see [Key Generation Overview and Algorithm Specifications](huks-key-generation-overview.md).

Alternatively, you can [import a key](huks-key-import-overview.md).

**Key derivation**

1. Obtain the key alias, specify the property parameter **HuksOptions**, and add the parameter [HUKS_TAG_KEY_ACCESS_GROUP](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukstag) to derive a group key.

2. Call [initSession](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksinitsession9) to initialize a key session and obtain the session handle.

3. Call [updateSession](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksupdatesession9) to update the key session.

4. Call [finishSession](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksfinishsession9) to finish the key session and derive a key.

**Key deletion**

Call [deleteKeyItem](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksdeletekeyitem9) to delete the key that is not required. For details, see [Deleting a Key (ArkTS)](huks-delete-key-arkts.md).

When deleting a key, specify [HUKS_TAG_KEY_ACCESS_GROUP](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukstag) to delete the group key.

### Development Cases

```ts
/*
 * Derive a PBKDF2 key using promise-based APIs.
 * Derive a group key using the group key.
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
 * Set a key alias and encapsulate the key property set.
 */
let srcKeyAlias = "pbkdf2Key";
let salt = "mySalt";
let iterationCount = 10000;
let derivedKeySize = 32;
let handle: number;
let finishOutData: Uint8Array;
/*
 * Add the group information to the assetAccessGroups field in app.json5.
 */
let group = 'ohos.test.groupKey';

/* Set the parameter set for key generation. */
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
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_ACCESS_GROUP,
    value: StringToUint8Array(group)
  }
];

let huksOptions: huks.HuksOptions = {
  properties: properties,
  inData: new Uint8Array(new Array())
}

/* Set the parameter set for initialization. */
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
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_ACCESS_GROUP,
    value: StringToUint8Array(group)
  }
];

let initOptions: huks.HuksOptions = {
  properties: initProperties,
  inData: new Uint8Array(new Array())
}

/* Set the parameter set for finish. */
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
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_ACCESS_GROUP,
    value: StringToUint8Array(group)
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
        console.error(`promise: generateKeyItem failed, errCode: ${error.code}, errMsg: ${error.message}`);
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
        console.error(`promise: initSession failed, errCode: ${error.code}, errMsg: ${error.message}`);
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
        console.error(`promise: updateSession failed, errCode: ${error.code}, errMsg: ${error.message}`);
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
        console.error(`promise: finishSession failed, errCode: ${error.code}, errMsg: ${error.message}`);
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
        console.error(`promise: deleteKeyItem failed, errCode: ${error.code}, errMsg: ${error.message}`);
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
