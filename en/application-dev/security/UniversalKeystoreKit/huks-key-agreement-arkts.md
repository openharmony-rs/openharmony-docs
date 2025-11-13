# Key Agreement (ArkTS)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

This topic uses X25519 and DH as an example to demonstrate how to perform key agreement for HUKS-managed keys. For details about the scenarios and supported algorithm specifications, see [Supported Algorithms](huks-key-agreement-overview.md#supported-algorithms).

## How to Develop

**Key Generation**

Generate an asymmetric key for device A and device B each. For details, see [Key Generation](huks-key-generation-overview.md) or [Key Import](huks-key-import-overview.md).

(Optional) You can specify the [HUKS_TAG_DERIVED_AGREED_KEY_STORAGE_FLAG](../../reference/apis-universal-keystore-kit/capi-native-huks-type-h.md#oh_huks_keystoragetype) parameter when generating a key to decide if HUKS manages the resulting key from the key agreement process.

- If this tag is set to **HUKS_STORAGE_ONLY_USED_IN_HUKS**, the shared secret is managed by HUKS. That is, the shared secret is always in a secure environment throughout its lifecycle.

- If this tag is set to **HUKS_STORAGE_KEY_EXPORT_ALLOWED**, the shared secret generated will be returned to the caller for management. That is, service side ensures the key security.

- If this tag is not set, the shared secret generated can be either managed by HUKS or returned to the caller for management. The key protection mode can be set in the subsequent key agreement on the service side.

**Key Export**

Export the public key of the asymmetric key pair of device A and device B. For details, see [Key Export](huks-export-key-arkts.md).

**Key Agreement**

Perform key agreement using the public key of the peer device and private key of the local device (that is, public key of device B and private key of device A for device A, and public key of device A and private key of device B for device B) to produce a shared secret.

During key agreement, you can set **HUKS_TAG_DERIVED_AGREED_KEY_STORAGE_FLAG** (optional) to specify how the shared secret generated is managed.

| Key Generation| Key Agreement| Specifications|
| -------- | -------- | -------- |
| HUKS_STORAGE_ONLY_USED_IN_HUKS | HUKS_STORAGE_ONLY_USED_IN_HUKS | The key is managed by HUKS.|
| HUKS_STORAGE_KEY_EXPORT_ALLOWED | HUKS_STORAGE_KEY_EXPORT_ALLOWED | The key is returned to the caller for management.|
| The tag is not set.| HUKS_STORAGE_ONLY_USED_IN_HUKS | The key is managed by HUKS.|
| The tag is not set.| HUKS_STORAGE_KEY_EXPORT_ALLOWED | The key is returned to the caller for management.|
| The tag is not set.| The tag is not set.| The key is returned to the caller for management.|

Note: The tag value set in key agreement should not conflict with the tag value set in key generation. The above table lists only valid settings.

**Key Deletion**

Delete the keys from device A and device B when the keys are not required. For details, see [Deleting a Key](huks-delete-key-arkts.md).


The following uses X25519 and DH key agreement as examples. 
### X25519 asymmetric key agreement example
```ts
/*
 * Agree on an X25519 key using promise-based APIs.
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
let srcKeyAliasFirst = "AgreeX25519KeyFirstAlias";
let srcKeyAliasSecond = "AgreeX25519KeySecondAlias";
let agreeX25519InData = 'AgreeX25519TestIndata';
let finishOutData: Uint8Array;
let handle: number;
let exportKey: Uint8Array;
let exportKeyFirst: Uint8Array;
let exportKeySecond: Uint8Array;
/* Set the parameter set used for generating the key. */
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
  }
];
let HuksOptions: huks.HuksOptions = {
  properties: properties,
  inData: new Uint8Array(new Array())
}
/* Set the parameter set for the first key agreement. */
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
  }
];
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
        console.error(`promise: generateKeyItem failed, errCode : ${error.code}, errMsg : ${error.message}`);
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
        console.error(`promise: initSession failed, errCode : ${error.code}, errMsg : ${error.message}`);
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
        console.error(`promise: updateSession failed, errCode : ${error.code}, errMsg : ${error.message}`);
      })
  } catch (error) {
    console.error(`promise: updateSession input arg invalid`);
  }
}

/* Finish the key session to output the shared secret key. */
async function finishSession(handle: number, huksOptions: huks.HuksOptions) {
  console.info("promise: enter finishSession");
  try {
    await huks.finishSession(handle, huksOptions)
      .then((data) => {
        finishOutData = data.outData as Uint8Array;
        console.info(`promise: finishSession success, data is ` + Uint8ArrayToString(data.outData as Uint8Array));
      }).catch((error: BusinessError) => {
        console.error(`promise: finishSession failed, errCode : ${error.code}, errMsg : ${error.message}`);
      })
  } catch (error) {
    console.error(`promise: finishSession input arg invalid`);
  }
}

/* Export a key. */
async function exportKeyItem(keyAlias: string, huksOptions: huks.HuksOptions) {
  console.info("promise: enter exportKeyItem");
  try {
    await huks.exportKeyItem(keyAlias, huksOptions)
      .then((data) => {
        exportKey = data.outData as Uint8Array;
        console.info(`promise: exportKey success, data is ` + Uint8ArrayToString(data.outData as Uint8Array));
      }).catch((error: BusinessError) => {
        console.error(`promise: exportKeyItem failed, errCode : ${error.code}, errMsg : ${error.message}`);
      })
  } catch (error) {
    console.error(`promise: exportKeyItem input arg invalid`);
  }
}

/* Delete the keys. */
async function deleteKeyItem(keyAlias: string, huksOptions: huks.HuksOptions) {
  console.info("promise: enter deleteKeyItem");
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

async function testAgree() {
  /* 1. Set the key alias srcKeyAliasFirst for device A and srcKeyAliasSecond for device B, and parameters for generating the key pairs. */
  /* 2. Generate an asymmetric key pair for device A. */
  await generateKeyItem(srcKeyAliasFirst, HuksOptions);
  /* 3. Generate an asymmetric key pair for device B. */
  await generateKeyItem(srcKeyAliasSecond, HuksOptions);
  /* 4. Export the public keys of the key pairs of device A and device B. */
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
  /* 7. Delete the keys on device A and device B. */
  await deleteKeyItem(srcKeyAliasFirst, HuksOptions);
  await deleteKeyItem(srcKeyAliasSecond, HuksOptions);
}
```

### DH key agreement example
```ts
/*
 * Agree on a DH key using promise-based APIs.
 */
import { huks } from '@kit.UniversalKeystoreKit';

function StringToUint8Array(str: string) {
  let arr: number[] = []
  for (let i = 0, j = str.length; i < j; ++i) {
    arr.push(str.charCodeAt(i))
  }
  return new Uint8Array(arr)
}

function Uint8ArrayToBigInt(arr: Uint8Array): bigint {
  let i = 0
  const byteMax: bigint = BigInt('0x100')
  let result: bigint = BigInt('0')
  while (i < arr.length) {
    result = result * byteMax
    result = result + BigInt(arr[i])
    i += 1
  }
  return result
}

const dhAgree: Array<huks.HuksParam> = [{
  tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
  value: huks.HuksKeyAlg.HUKS_ALG_DH,
}, {
  tag: huks.HuksTag.HUKS_TAG_PURPOSE,
  value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_AGREE,
}]
const dh2048Agree: Array<huks.HuksParam> = [
  ...dhAgree, {
  tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
  value: huks.HuksKeySize.HUKS_DH_KEY_SIZE_2048,
}]
const dhGenOptions: huks.HuksOptions = {
  properties: dh2048Agree,
  inData: new Uint8Array([])
}
const emptyOptions: huks.HuksOptions = {
  properties: [],
  inData: new Uint8Array([])
}

async function HuksDhAgreeExportKey(keyAlias: string,
  peerPubKey: huks.HuksReturnResult): Promise<huks.HuksReturnResult> {
  const initHandle = await huks.initSession(keyAlias, dhGenOptions)
  const dhAgreeUpdateBobPubKey: huks.HuksOptions = {
    properties: [
      ...dh2048Agree, {
      tag: huks.HuksTag.HUKS_TAG_DERIVED_AGREED_KEY_STORAGE_FLAG,
      value: huks.HuksKeyStorageType.HUKS_STORAGE_KEY_EXPORT_ALLOWED,
    }],
    inData: peerPubKey.outData
  }
  await huks.updateSession(initHandle.handle, dhAgreeUpdateBobPubKey)
  return await huks.finishSession(initHandle.handle, emptyOptions)
}

async function HuksDhAgreeExportTest(
  aliasA: string, aliasB: string,
  pubKeyA: huks.HuksReturnResult, pubKeyB: huks.HuksReturnResult) {

  const agreedKeyFromAlice = await HuksDhAgreeExportKey(aliasA, pubKeyB)
  console.info(`ok! agreedKeyFromAlice export is 0x${Uint8ArrayToBigInt(agreedKeyFromAlice.outData).toString(16)}`)

  const agreedKeyFromBob = await HuksDhAgreeExportKey(aliasB, pubKeyA)
  console.info(`ok! agreedKeyFromBob export is 0x${Uint8ArrayToBigInt(agreedKeyFromBob.outData).toString(16)}`)
}

async function HuksDhAgreeInHuks(keyAlias: string, peerPubKey: huks.HuksReturnResult,
  aliasAgreedKey: string): Promise<huks.HuksReturnResult> {
  const onlyUsedInHuks: Array<huks.HuksParam> = [{
    tag: huks.HuksTag.HUKS_TAG_KEY_STORAGE_FLAG,
    value: huks.HuksKeyStorageType.HUKS_STORAGE_ONLY_USED_IN_HUKS,
  }, {
    tag: huks.HuksTag.HUKS_TAG_DERIVED_AGREED_KEY_STORAGE_FLAG,
    value: huks.HuksKeyStorageType.HUKS_STORAGE_ONLY_USED_IN_HUKS,
  }]
  const dhAgreeInit: huks.HuksOptions = {
    properties: [
      ...dhAgree,
      { tag: huks.HuksTag.HUKS_TAG_KEY_SIZE, value: huks.HuksKeySize.HUKS_AES_KEY_SIZE_256, },
      ...onlyUsedInHuks],
    inData: new Uint8Array([])
  }
  const dhAgreeFinishParams: Array<huks.HuksParam> = [
    ...onlyUsedInHuks,
    { tag: huks.HuksTag.HUKS_TAG_IS_KEY_ALIAS, value: true },
    { tag: huks.HuksTag.HUKS_TAG_ALGORITHM, value: huks.HuksKeyAlg.HUKS_ALG_AES },
    { tag: huks.HuksTag.HUKS_TAG_KEY_SIZE, value: huks.HuksKeySize.HUKS_AES_KEY_SIZE_256 },
    {
      tag: huks.HuksTag.HUKS_TAG_PURPOSE,
      value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT | huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_DECRYPT
    }
  ]

  const handle = await huks.initSession(keyAlias, dhAgreeInit)
  const dhAgreeUpdatePubKey: huks.HuksOptions = {
    properties: [...dhAgree, ...onlyUsedInHuks],
    inData: peerPubKey.outData
  }
  await huks.updateSession(handle.handle, dhAgreeUpdatePubKey)
  const dhAgreeAliceFinnish: huks.HuksOptions = {
    properties: [...dhAgreeFinishParams, {
      tag: huks.HuksTag.HUKS_TAG_KEY_ALIAS, value: StringToUint8Array(aliasAgreedKey)
    }], inData: new Uint8Array([])
  }
  return await huks.finishSession(handle.handle, dhAgreeAliceFinnish)
}

async function HuksDhAgreeInHuksTest(
  aliasA: string, aliasB: string,
  pubKeyA: huks.HuksReturnResult, pubKeyB: huks.HuksReturnResult,
  aliasAgreedKeyFromA: string, aliasAgreedKeyFromB: string) {

  const finishAliceResult = await HuksDhAgreeInHuks(aliasA, pubKeyB, aliasAgreedKeyFromA)
  console.info(`ok! finishAliceResult in huks is 0x${Uint8ArrayToBigInt(finishAliceResult.outData).toString(16)}`)
  const aliceAgreedExist = await huks.isKeyItemExist(aliasAgreedKeyFromA, emptyOptions)
  console.info(`ok! aliceAgreedExist in huks is ${aliceAgreedExist}`)

  const finishBobResult = await HuksDhAgreeInHuks(aliasB, pubKeyA, aliasAgreedKeyFromB)
  console.info(`ok! finishBobResult in huks is 0x${Uint8ArrayToBigInt(finishBobResult.outData).toString(16)}`)
  const bobAgreedExist = await huks.isKeyItemExist(aliasAgreedKeyFromB, emptyOptions)
  console.info(`ok! bobAgreedExist in huks is ${bobAgreedExist}`)

  await huks.deleteKeyItem(aliasAgreedKeyFromA, emptyOptions)
  await huks.deleteKeyItem(aliasAgreedKeyFromB, emptyOptions)
}

async function HuksDhAgreeTest() {
  const aliasAlice = 'alice'
  const aliasBob = 'bob'

  /* Call generateKeyItem to generate a key with alias of alice and a key with alias of bob. */
  await huks.generateKeyItem(aliasAlice, dhGenOptions)
  await huks.generateKeyItem(aliasBob, dhGenOptions)

  /* Export the public keys of asymmetric key pairs alice and bob. */
  const pubKeyAlice = await huks.exportKeyItem(aliasAlice, emptyOptions)
  const pubKeyBob = await huks.exportKeyItem(aliasBob, emptyOptions)

  /* Perform key agreement and return the shared secret generated to the caller for management. */
  await HuksDhAgreeExportTest(aliasAlice, aliasBob, pubKeyAlice, pubKeyBob)

  /* Perform key agreement and let HUKS manage the shared secret generated. */
  await HuksDhAgreeInHuksTest(aliasAlice, aliasBob, pubKeyAlice, pubKeyBob, 'agreedKeyFromAlice', 'agreedKeyFromBob')

  await huks.deleteKeyItem(aliasAlice, emptyOptions)
  await huks.deleteKeyItem(aliasBob, emptyOptions)
}
```
