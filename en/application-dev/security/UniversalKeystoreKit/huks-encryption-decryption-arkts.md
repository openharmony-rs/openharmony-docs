# Encryption and Decryption (ArkTS)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

This topic uses AES-128, RSA-2048, SM2, and DES64 as examples to describe the encryption and decryption workflows. For details about the scenarios and supported algorithms, see [Supported Algorithms](huks-encryption-decryption-overview.md#supported-algorithms).

## How to Develop

**Key Generation**

1. Specify the key alias. For details about the naming rules, see [Key Generation Overview and Algorithm Specifications](huks-key-generation-overview.md).

2. Initialize the key property set.

3. Use [generateKeyItem](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksgeneratekeyitem9) to generate a key. For details, see [Key Generation](huks-key-generation-overview.md).

Alternatively, you can [import a key](huks-key-import-overview.md).

**Encryption**

1. Obtain the key alias.

2. Obtain the data to be encrypted.

3. Obtain the [algorithm parameters](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksparam) for encryption.

   The parameters to be configured vary with the algorithm used.
   - If the AES algorithm is used for encryption, the block mode is CBC, and the padding mode is PKCS7, the **IV** parameter is mandatory. For details, see [AES/CBC/PKCS7](#aescbcpkcs7).
   - If the AES algorithm is used for encryption and the block mode is GCM, the **NONCE** and **AAD** parameters are optional. For details, see [AES/GCM/NoPadding](#aesgcmnopadding).
   - If the AES algorithm is used for encryption and the block mode is CCM, the **NONCE** and **AAD** parameters are optional. For details, see [AES/CCM/NoPadding](#aesccmnopadding).
   - If the RSA algorithm is used for encryption, you need to select the corresponding block mode, padding mode, and digest algorithm. For details, see [RSA/ECB/PKCS1_V1_5](#rsaecbpkcs1_v1_5) and [RSA/ECB/OAEP/SHA256](#rsaecboaepsha256).
   - If the SM2 algorithm is used for encryption, the digest algorithm must be SM3. For details, see [SM2](#sm2).
   <!--Del-->
   - If the DES algorithm is used for encryption and the block mode is CBC, the **IV** parameter is mandatory. For details, see [DES/CBC/NoPadding](#descbcnopadding).
   <!--DelEnd-->
   
   For details about the specifications, see [Encryption and Decryption Overview and Algorithm Specifications](huks-encryption-decryption-overview.md).

4. Use [initSession](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksinitsession9) to initialize a key session. The session handle is returned after the initialization.

5. Use [finishSession](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksfinishsession9) with the session handle to obtain the ciphertext.

**Decryption**

1. Obtain the key alias.

2. Obtain the ciphertext to be decrypted.

3. Obtain the [algorithm parameters](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksparam) for decryption.

   The parameters to be configured vary with the algorithm used.
   - If the AES algorithm and GCM block mode are used for decryption, **NONCE** and **AEAD** are mandatory and **AAD** is optional. For details, see [AES/GCM/NoPadding](#aesgcmnopadding).
   - The requirements for the parameters in the other development cases are the same as those in the encryption.
   
   For details about the specifications, see [Encryption and Decryption Overview and Algorithm Specifications](huks-encryption-decryption-overview.md).

4. Use [initSession](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksinitsession9) to initialize a key session. The session handle is returned after the initialization.

5. Use [finishSession](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksfinishsession9) to obtain the data decrypted.

**Key Deletion**

Use [deleteKeyItem](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksdeletekeyitem9) to delete the key that is not required. For details, see [Deleting a Key](huks-delete-key-arkts.md).

## Development Cases

### AES/CBC/PKCS7
<!-- @[encrypt_and_decrypt_AESCBCPKCS7](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/KeyUsage/EncryptionDecryption/entry/src/main/ets/pages/AESCBCPKCS7.ets) -->

``` TypeScript
/*
 * The following uses AES/CBC/PKCS7 with promise-based APIs.
 */
import { huks } from '@kit.UniversalKeystoreKit';
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { BusinessError } from '@kit.BasicServicesKit';

let aesKeyAlias = 'test_aesKeyAlias';
let handle: number;
let plainText = '123456';
let IV = cryptoFramework.createRandom().generateRandomSync(12).data;
let cipherData: Uint8Array;

function stringToUint8Array(str: string) {
  let arr: number[] = [];
  for (let i = 0, j = str.length; i < j; ++i) {
    arr.push(str.charCodeAt(i));
  }
  return new Uint8Array(arr);
}

function uint8ArrayToString(fileData: Uint8Array) {
  let dataString = '';
  for (let i = 0; i < fileData.length; i++) {
    dataString += String.fromCharCode(fileData[i]);
  }
  return dataString;
}

function getAesGenerateProperties() {
  let properties: huks.HuksParam[] = [{
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_AES
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_AES_KEY_SIZE_128
  }, {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT |
    huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_DECRYPT
  }];
  return properties;
}

function getAesEncryptProperties() {
  let properties: huks.HuksParam[] = [{
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
  }];
  return properties;
}

function getAesDecryptProperties() {
  let properties: huks.HuksParam[] = [{
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
  }];
  return properties;
}

async function generateAesKey() {
  /*
   * Simulate the key generation scenario.
   */
  /*
   * 1. Obtain the parameters for key generation.
   */
  let genProperties = getAesGenerateProperties();
  let options: huks.HuksOptions = {
    properties: genProperties
  }
  /*
   * 2. Call generateKeyItem.
   */
  await huks.generateKeyItem(aesKeyAlias, options)
    .then(() => {
      console.info(`promise: generate AES Key success`);
    }).catch((error: BusinessError) => {
      console.error(`promise: generate AES Key failed, errCode : ${error.code}, errMsg : ${error.message}`);
    })
}

async function encryptData() {
  /*
   * Simulate the encryption scenario.
   */
  /*
   * 1. Obtain the algorithm parameters for encryption.
   */
  let encryptProperties = getAesEncryptProperties();
  let options: huks.HuksOptions = {
    properties: encryptProperties,
    inData: stringToUint8Array(plainText)
  }
  /*
   * 2. Call initSession to obtain a session handle.
   */
  await huks.initSession(aesKeyAlias, options)
    .then((data) => {
      handle = data.handle;
    }).catch((error: BusinessError) => {
      console.error(`promise: init EncryptData failed, errCode : ${error.code}, errMsg : ${error.message}`);
    })
  /*
   * 3. Call finishSession to obtain the ciphertext.
   */
  await huks.finishSession(handle, options)
    .then((data) => {
      console.info(`promise: encrypt data success, data is ` + uint8ArrayToString(data.outData as Uint8Array));
      cipherData = data.outData as Uint8Array;
    }).catch((error: BusinessError) => {
      console.error(`promise: encrypt data failed, errCode : ${error.code}, errMsg : ${error.message}`);
    })
}

async function decryptData() {
  /*
   * Simulate the decryption scenario.
   * 1. Obtain the key alias.
   */
  /*
   * 1. Obtain the algorithm parameters for decryption.
   */
  let decryptOptions = getAesDecryptProperties()
  let options: huks.HuksOptions = {
    properties: decryptOptions,
    inData: cipherData
  }
  /*
   * 2. Call initSession to obtain a session handle.
   */
  await huks.initSession(aesKeyAlias, options)
    .then((data) => {
      handle = data.handle;
    }).catch((error: BusinessError) => {
      console.error(`promise: init DecryptData failed, errCode : ${error.code}, errMsg : ${error.message}`);
    })
  /*
   * 3. Call finishSession to obtain the decrypted data.
   */
  await huks.finishSession(handle, options)
    .then((data) => {
      console.info(`promise: decrypt data success, data is ` + uint8ArrayToString(data.outData as Uint8Array));
    }).catch((error: BusinessError) => {
      console.error(`promise: decrypt data failed, errCode : ${error.code}, errMsg : ${error.message}`);
    })
}

async function deleteKey() {
  /*
   * Simulate the key deletion scenario.
   */
  let emptyOptions: huks.HuksOptions = {
    properties: []
  }
  /*
   * 1. Call deleteKeyItem to delete the key.
   */
  await huks.deleteKeyItem(aesKeyAlias, emptyOptions)
    .then(() => {
      console.info(`promise: delete data success`);
    }).catch((error: BusinessError) => {
      console.error(`promise: delete data failed, errCode : ${error.code}, errMsg : ${error.message}`);
    })
}
```
<!-- -->

### AES/GCM/NoPadding
<!-- @[encrypt_and_decrypt_AESGCMNoPadding](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/KeyUsage/EncryptionDecryption/entry/src/main/ets/pages/AESGCMNoPadding.ets) -->

``` TypeScript
/*
 * The following uses AES/GCM/NoPadding with promise-based APIs.
 */
import { huks } from '@kit.UniversalKeystoreKit';
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { BusinessError } from '@kit.BasicServicesKit';

let aesKeyAlias = 'test_aesKeyAlias';
let handle: number;
let plainText = '123456';
let cipherData: Uint8Array;
let AAD = '1234567890123456';
let NONCE = cryptoFramework.createRandom().generateRandomSync(12).data;

function stringToUint8Array(str: string) {
  let arr: number[] = [];
  for (let i = 0, j = str.length; i < j; ++i) {
    arr.push(str.charCodeAt(i));
  }
  return new Uint8Array(arr);
}

function uint8ArrayToString(fileData: Uint8Array) {
  let dataString = '';
  for (let i = 0; i < fileData.length; i++) {
    dataString += String.fromCharCode(fileData[i]);
  }
  return dataString;
}

function getAesGenerateProperties() {
  let properties: huks.HuksParam[] = [{
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_AES
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_AES_KEY_SIZE_128
  }, {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT |
    huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_DECRYPT
  }];
  return properties;
}

function getAesGcmEncryptProperties() {
  let properties: huks.HuksParam[] = [{
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
    value: huks.HuksKeyPadding.HUKS_PADDING_NONE
  }, {
    tag: huks.HuksTag.HUKS_TAG_BLOCK_MODE,
    value: huks.HuksCipherMode.HUKS_MODE_GCM
  }, {
    tag: huks.HuksTag.HUKS_TAG_NONCE,
    value: NONCE
  }, {
    tag: huks.HuksTag.HUKS_TAG_ASSOCIATED_DATA,
    value: stringToUint8Array(AAD)
  }];
  return properties;
}

function getAesGcmDecryptProperties(cipherData: Uint8Array) {
  let properties: huks.HuksParam[] = [{
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
    value: huks.HuksKeyPadding.HUKS_PADDING_NONE
  }, {
    tag: huks.HuksTag.HUKS_TAG_BLOCK_MODE,
    value: huks.HuksCipherMode.HUKS_MODE_GCM
  }, {
    tag: huks.HuksTag.HUKS_TAG_NONCE,
    value: NONCE
  }, {
    tag: huks.HuksTag.HUKS_TAG_ASSOCIATED_DATA,
    value: stringToUint8Array(AAD)
  }, {
    tag: huks.HuksTag.HUKS_TAG_AE_TAG,
    value: cipherData.slice(cipherData.length - 16)
  }];
  return properties;
}

async function generateAesKey() {
  /*
   * Simulate the key generation scenario.
   */
  /*
   * 1. Obtain the parameters for key generation.
   */
  let genProperties = getAesGenerateProperties();
  let options: huks.HuksOptions = {
    properties: genProperties
  }
  /*
   * 2. Call generateKeyItem.
   */
  await huks.generateKeyItem(aesKeyAlias, options)
    .then(() => {
      console.info(`promise: generate AES Key success`);
    }).catch((error: BusinessError) => {
      console.error(`promise: generate AES Key failed, errCode : ${error.code}, errMsg : ${error.message}`);
    })
}

async function encryptData() {
  /*
   * Simulate the encryption scenario.
   */
  /*
   * 1. Obtain the algorithm parameters for encryption.
   */
  let encryptProperties = getAesGcmEncryptProperties();
  let options: huks.HuksOptions = {
    properties: encryptProperties,
    inData: stringToUint8Array(plainText)
  }
  /*
   * 2. Call initSession to obtain a session handle.
   */
  await huks.initSession(aesKeyAlias, options)
    .then((data) => {
      handle = data.handle;
    }).catch((error: BusinessError) => {
      console.error(`promise: init EncryptDataGcm failed, errCode : ${error.code}, errMsg : ${error.message}`);
    })
  /*
   * 3. Call finishSession to obtain the ciphertext.
   */
  await huks.finishSession(handle, options)
    .then((data) => {
      console.info(`promise: encrypt data success, data is ` + uint8ArrayToString(data.outData as Uint8Array));
      cipherData = data.outData as Uint8Array;
    }).catch((error: BusinessError) => {
      console.error(`promise: encrypt data failed, errCode : ${error.code}, errMsg : ${error.message}`);
    })
}

async function decryptData() {
  /*
   * Simulate the decryption scenario.
   */
  /*
   * 1. Obtain the algorithm parameters for decryption.
   */
  let decryptOptions = getAesGcmDecryptProperties(cipherData)
  let options: huks.HuksOptions = {
    properties: decryptOptions,
    inData: cipherData.slice(0, cipherData.length - 16)
  }
  /*
   * 2. Call initSession to obtain a session handle.
   */
  await huks.initSession(aesKeyAlias, options)
    .then((data) => {
      handle = data.handle;
    }).catch((error: BusinessError) => {
      console.error(`promise: init DecryptDataGcm failed, errCode : ${error.code}, errMsg : ${error.message}`);
    })
  /*
   * 3. Call finishSession to obtain the decrypted data.
   */
  await huks.finishSession(handle, options)
    .then((data) => {
      console.info(`promise: decrypt data success, data is ` + uint8ArrayToString(data.outData as Uint8Array));
    }).catch((error: BusinessError) => {
      console.error(`promise: decrypt data failed, errCode : ${error.code}, errMsg : ${error.message}`);
    })
}

async function deleteKey() {
  /*
   * Simulate the key deletion scenario.
   */
  let emptyOptions: huks.HuksOptions = {
    properties: []
  }
  /*
   * 1. Call deleteKeyItem to delete the key.
   */
  await huks.deleteKeyItem(aesKeyAlias, emptyOptions)
    .then(() => {
      console.info(`promise: delete data success`);
    }).catch((error: BusinessError) => {
      console.error(`promise: delete data failed, errCode : ${error.code}, errMsg : ${error.message}`);
    })
}
```
<!-- -->

### AES/CCM/NoPadding

```ts
/*
 * The following uses AES/CCM/NoPadding with promise-based APIs as an example.
 */
import { huks } from '@kit.UniversalKeystoreKit';
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { BusinessError } from "@kit.BasicServicesKit";

let aesKeyAlias = 'test_aesCcmKeyAlias';
let handle: number;
let plainText = '123456';
let cipherData: Uint8Array;
let AAD = '1234567890123456';
let NONCE = cryptoFramework.createRandom().generateRandomSync(12).data;
let aeadTagLen = 14;

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
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT |
    huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_DECRYPT
  }];
  return properties;
}

function GetAesCcmEncryptProperties() {
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
    value: huks.HuksKeyPadding.HUKS_PADDING_NONE
  }, {
    tag: huks.HuksTag.HUKS_TAG_BLOCK_MODE,
    value: huks.HuksCipherMode.HUKS_MODE_CCM
  }, {
    tag: huks.HuksTag.HUKS_TAG_NONCE,
    value: NONCE
  }, {
    tag: huks.HuksTag.HUKS_TAG_ASSOCIATED_DATA,
    value: StringToUint8Array(AAD)
  }, {
    tag: huks.HuksTag.HUKS_TAG_AE_TAG_LEN,
    value: aeadTagLen
  }];
  return properties;
}

function GetAesCcmDecryptProperties(cipherData: Uint8Array) {
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
    value: huks.HuksKeyPadding.HUKS_PADDING_NONE
  }, {
    tag: huks.HuksTag.HUKS_TAG_BLOCK_MODE,
    value: huks.HuksCipherMode.HUKS_MODE_CCM
  }, {
    tag: huks.HuksTag.HUKS_TAG_NONCE,
    value: NONCE
  }, {
    tag: huks.HuksTag.HUKS_TAG_ASSOCIATED_DATA,
    value: StringToUint8Array(AAD)
  }, {
    tag: huks.HuksTag.HUKS_TAG_AE_TAG,
    value: cipherData.slice(cipherData.length - aeadTagLen)
  }, {
    tag: huks.HuksTag.HUKS_TAG_AE_TAG_LEN,
    value: aeadTagLen
  }];
  return properties;
}

async function GenerateAesKey() {
  /*
   * Simulate the key generation scenario.
   * 1. Set the key alias.
   */
  /*
   * 2. Obtain the parameters for key generation.
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
      console.error(`promise: generate AES Key failed, errCode : ${error.code}, errMsg : ${error.message}`);
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
  let encryptProperties = GetAesCcmEncryptProperties();
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
      console.error(`promise: init EncryptDataCcm failed, errCode : ${error.code}, errMsg : ${error.message}`);
    })
  /*
   * 5. Call finishSession to obtain the ciphertext.
   */
  await huks.finishSession(handle, options)
    .then((data) => {
      console.info(`promise: encrypt data success, data is ` + Uint8ArrayToString(data.outData as Uint8Array));
      cipherData = data.outData as Uint8Array;
    }).catch((error: BusinessError) => {
      console.error(`promise: encrypt data failed, errCode : ${error.code}, errMsg : ${error.message}`);
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
  let decryptOptions = GetAesCcmDecryptProperties(cipherData)
  let options: huks.HuksOptions = {
    properties: decryptOptions,
    inData: cipherData.slice(0, cipherData.length - aeadTagLen)
  }
  /*
   * 4. Call initSession to obtain a session handle.
   */
  await huks.initSession(aesKeyAlias, options)
    .then((data) => {
      handle = data.handle;
    }).catch((error: BusinessError) => {
      console.error(`promise: init DecryptDataCcm failed, errCode : ${error.code}, errMsg : ${error.message}`);
    })
  /*
   * 5. Call finishSession to obtain the decrypted data.
   */
  await huks.finishSession(handle, options)
    .then((data) => {
      console.info(`promise: decrypt data success, data is ` + Uint8ArrayToString(data.outData as Uint8Array));
    }).catch((error: BusinessError) => {
      console.error(`promise: decrypt data failed, errCode : ${error.code}, errMsg : ${error.message}`);
    })
}

async function DeleteKey() {
  /*
   * Simulate the key deletion scenario.
   * 1. Obtain the key alias.
   */
  let emptyOptions: huks.HuksOptions = {
    properties: []
  }
  /*
   * 2. Call deleteKeyItem to delete the key.
   */
  await huks.deleteKeyItem(aesKeyAlias, emptyOptions)
    .then(() => {
      console.info(`promise: delete data success`);
    }).catch((error: BusinessError) => {
      console.error(`promise: delete data failed, errCode : ${error.code}, errMsg : ${error.message}`);
    })
}

async function TestEncryptDecrypt() {
  await GenerateAesKey();
  await EncryptData();
  await DecryptData();
  await DeleteKey();
}
```

### RSA/ECB/PKCS1_V1_5
<!-- @[encrypt_and_decrypt_RSAECBPKCS1_V1_5](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/KeyUsage/EncryptionDecryption/entry/src/main/ets/pages/RSAECBPKCS1_V1_5.ets) -->

``` TypeScript
/*
 * The following uses RSA/ECB/PKCS1_V1_5 with promise-based APIs.
 */
import { huks } from '@kit.UniversalKeystoreKit';
import { BusinessError } from '@kit.BasicServicesKit';

let rsaKeyAlias = 'test_rsaKeyAlias';
let handle: number;
let plainText = '123456';
let cipherData: Uint8Array;

function stringToUint8Array(str: string) {
  let arr: number[] = [];
  for (let i = 0, j = str.length; i < j; ++i) {
    arr.push(str.charCodeAt(i));
  }
  return new Uint8Array(arr);
}

function uint8ArrayToString(fileData: Uint8Array) {
  let dataString = '';
  for (let i = 0; i < fileData.length; i++) {
    dataString += String.fromCharCode(fileData[i]);
  }
  return dataString;
}

function getRsaGenerateProperties() {
  let properties: huks.HuksParam[] = [{
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_RSA
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_RSA_KEY_SIZE_2048
  }, {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT |
    huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_DECRYPT
  }];
  return properties;
}

function getRsaEncryptProperties() {
  let properties: huks.HuksParam[] = [{
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_RSA
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_RSA_KEY_SIZE_2048
  }, {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT
  }, {
    tag: huks.HuksTag.HUKS_TAG_PADDING,
    value: huks.HuksKeyPadding.HUKS_PADDING_PKCS1_V1_5
  }, {
    tag: huks.HuksTag.HUKS_TAG_BLOCK_MODE,
    value: huks.HuksCipherMode.HUKS_MODE_ECB
  }, {
    tag: huks.HuksTag.HUKS_TAG_DIGEST,
    value: huks.HuksKeyDigest.HUKS_DIGEST_NONE
  }];
  return properties;
}

function getRsaDecryptProperties() {
  let properties: huks.HuksParam[] = [{
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_RSA
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_RSA_KEY_SIZE_2048
  }, {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_DECRYPT
  }, {
    tag: huks.HuksTag.HUKS_TAG_PADDING,
    value: huks.HuksKeyPadding.HUKS_PADDING_PKCS1_V1_5
  }, {
    tag: huks.HuksTag.HUKS_TAG_BLOCK_MODE,
    value: huks.HuksCipherMode.HUKS_MODE_ECB
  }, {
    tag: huks.HuksTag.HUKS_TAG_DIGEST,
    value: huks.HuksKeyDigest.HUKS_DIGEST_NONE
  }];
  return properties;
}

async function generateRsaKey() {
  /*
   * Simulate the key generation scenario.
   */
  /*
   * 1. Obtain the parameters for key generation.
   */
  let genProperties = getRsaGenerateProperties();
  let options: huks.HuksOptions = {
    properties: genProperties
  }
  /*
   * 2. Call generateKeyItem.
   */
  await huks.generateKeyItem(rsaKeyAlias, options)
    .then(() => {
      console.info(`promise: generate RSA Key success`);
    }).catch((error: BusinessError) => {
      console.error(`promise: generate RSA Key failed, errCode : ${error.code}, errMsg : ${error.message}`);
    })
}

async function encryptData() {
  /*
   * Simulate the encryption scenario.
   */
  /*
   * 1. Obtain the algorithm parameters for encryption.
   */
  let encryptProperties = getRsaEncryptProperties();
  let options: huks.HuksOptions = {
    properties: encryptProperties,
    inData: stringToUint8Array(plainText)
  }
  /*
   * 2. Call initSession to obtain a session handle.
   */
  await huks.initSession(rsaKeyAlias, options)
    .then((data) => {
      handle = data.handle;
    }).catch((error: BusinessError) => {
      console.error(`promise: init EncryptDataRsa failed, errCode : ${error.code}, errMsg : ${error.message}`);
    })
  /*
   * 3. Call finishSession to obtain the ciphertext.
   */
  await huks.finishSession(handle, options)
    .then((data) => {
      console.info(`promise: encrypt data success, data is ` + uint8ArrayToString(data.outData as Uint8Array));
      cipherData = data.outData as Uint8Array;
    }).catch((error: BusinessError) => {
      console.error(`promise: encrypt data failed, errCode : ${error.code}, errMsg : ${error.message}`);
    })
}

async function decryptData() {
  /*
   * Simulate the decryption scenario.
   */
  /*
   * 1. Obtain the algorithm parameters for decryption.
   */
  let decryptOptions = getRsaDecryptProperties()
  let options: huks.HuksOptions = {
    properties: decryptOptions,
    inData: cipherData
  }
  /*
   * 2. Call initSession to obtain a session handle.
   */
  await huks.initSession(rsaKeyAlias, options)
    .then((data) => {
      handle = data.handle;
    }).catch((error: BusinessError) => {
      console.error(`promise: init DecryptDataRsa failed, errCode : ${error.code}, errMsg : ${error.message}`);
    })
  /*
   * 3. Call finishSession to obtain the decrypted data.
   */
  await huks.finishSession(handle, options)
    .then((data) => {
      console.info(`promise: decrypt data success, data is ` + uint8ArrayToString(data.outData as Uint8Array));
    }).catch((error: BusinessError) => {
      console.error(`promise: decrypt data failed, errCode : ${error.code}, errMsg : ${error.message}`);
    })
}

async function deleteKey() {
  /*
   * Simulate the key deletion scenario.
   */
  let emptyOptions: huks.HuksOptions = {
    properties: []
  }
  /*
   * 1. Call deleteKeyItem to delete the key.
   */
  await huks.deleteKeyItem(rsaKeyAlias, emptyOptions)
    .then(() => {
      console.info(`promise: delete data success`);
    }).catch((error: BusinessError) => {
      console.error(`promise: delete data failed, errCode : ${error.code}, errMsg : ${error.message}`);
    })
}
```
<!-- -->

### RSA/ECB/OAEP/SHA256
<!-- @[encrypt_and_decrypt_RSAECBOAEPSHA256](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/KeyUsage/EncryptionDecryption/entry/src/main/ets/pages/RSAECBOAEPSHA256.ets) -->

``` TypeScript
/*
 * The following uses RSA/ECB/OAEP/SHA-256 with promise-based APIs.
 */
import { huks } from '@kit.UniversalKeystoreKit';
import { BusinessError } from '@kit.BasicServicesKit';

let rsaKeyAlias = 'test_rsaKeyAlias';
let handle: number;
let plainText = '123456';
let cipherData: Uint8Array;

function stringToUint8Array(str: string) {
  let arr: number[] = [];
  for (let i = 0, j = str.length; i < j; ++i) {
    arr.push(str.charCodeAt(i));
  }
  return new Uint8Array(arr);
}

function uint8ArrayToString(fileData: Uint8Array) {
  let dataString = '';
  for (let i = 0; i < fileData.length; i++) {
    dataString += String.fromCharCode(fileData[i]);
  }
  return dataString;
}

function getRsaGenerateProperties() {
  let properties: huks.HuksParam[] = [{
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_RSA
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_RSA_KEY_SIZE_2048
  }, {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT |
    huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_DECRYPT
  }];
  return properties;
}

function getRsaEncryptProperties() {
  let properties: huks.HuksParam[] = [{
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_RSA
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_RSA_KEY_SIZE_2048
  }, {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT
  }, {
    tag: huks.HuksTag.HUKS_TAG_PADDING,
    value: huks.HuksKeyPadding.HUKS_PADDING_OAEP
  }, {
    tag: huks.HuksTag.HUKS_TAG_BLOCK_MODE,
    value: huks.HuksCipherMode.HUKS_MODE_ECB
  }, {
    tag: huks.HuksTag.HUKS_TAG_DIGEST,
    value: huks.HuksKeyDigest.HUKS_DIGEST_SHA256
  }];
  return properties;
}

function getRsaDecryptProperties() {
  let properties: huks.HuksParam[] = [{
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_RSA
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_RSA_KEY_SIZE_2048
  }, {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_DECRYPT
  }, {
    tag: huks.HuksTag.HUKS_TAG_PADDING,
    value: huks.HuksKeyPadding.HUKS_PADDING_OAEP
  }, {
    tag: huks.HuksTag.HUKS_TAG_BLOCK_MODE,
    value: huks.HuksCipherMode.HUKS_MODE_ECB
  }, {
    tag: huks.HuksTag.HUKS_TAG_DIGEST,
    value: huks.HuksKeyDigest.HUKS_DIGEST_SHA256
  }];
  return properties;
}

async function generateRsaKey() {
  /*
   * Simulate the key generation scenario.
   */
  /*
   * 1. Obtain the parameters for key generation.
   */
  let genProperties = getRsaGenerateProperties();
  let options: huks.HuksOptions = {
    properties: genProperties
  }
  /*
   * 2. Call generateKeyItem.
   */
  await huks.generateKeyItem(rsaKeyAlias, options)
    .then(() => {
      console.info(`promise: generate RSA Key success`);
    }).catch((error: BusinessError) => {
      console.error(`promise: generate RSA Key failed, errCode : ${error.code}, errMsg : ${error.message}`);
    })
}

async function encryptData() {
  /*
   * Simulate the encryption scenario.
   */
  /*
   * 1. Obtain the algorithm parameters for encryption.
   */
  let encryptProperties = getRsaEncryptProperties();
  let options: huks.HuksOptions = {
    properties: encryptProperties,
    inData: stringToUint8Array(plainText)
  }
  /*
   * 2. Call initSession to obtain a session handle.
   */
  await huks.initSession(rsaKeyAlias, options)
    .then((data) => {
      handle = data.handle;
    }).catch((error: BusinessError) => {
      console.error(`promise: init EncryptDataRsa failed, errCode : ${error.code}, errMsg : ${error.message}`);
    })
  /*
   * 3. Call finishSession to obtain the ciphertext.
   */
  await huks.finishSession(handle, options)
    .then((data) => {
      console.info(`promise: encrypt data success, data is ` + uint8ArrayToString(data.outData as Uint8Array));
      cipherData = data.outData as Uint8Array;
    }).catch((error: BusinessError) => {
      console.error(`promise: encrypt data failed, errCode : ${error.code}, errMsg : ${error.message}`);
    })
}

async function decryptData() {
  /*
   * Simulate the decryption scenario.
   */
  /*
   * 1. Obtain the algorithm parameters for decryption.
   */
  let decryptOptions = getRsaDecryptProperties()
  let options: huks.HuksOptions = {
    properties: decryptOptions,
    inData: cipherData
  }
  /*
   * 2. Call initSession to obtain a session handle.
   */
  await huks.initSession(rsaKeyAlias, options)
    .then((data) => {
      handle = data.handle;
    }).catch((error: BusinessError) => {
      console.error(`promise: init DecryptDataRsa failed, errCode : ${error.code}, errMsg : ${error.message}`);
    })
  /*
   * 3. Call finishSession to obtain the decrypted data.
   */
  await huks.finishSession(handle, options)
    .then((data) => {
      console.info(`promise: decrypt data success, data is ` + uint8ArrayToString(data.outData as Uint8Array));
    }).catch((error: BusinessError) => {
      console.error(`promise: decrypt data failed, errCode : ${error.code}, errMsg : ${error.message}`);
    })
}

async function deleteKey() {
  /*
   * Simulate the key deletion scenario.
   */
  let emptyOptions: huks.HuksOptions = {
    properties: []
  }
  /*
   * 1. Call deleteKeyItem to delete the key.
   */
  await huks.deleteKeyItem(rsaKeyAlias, emptyOptions)
    .then((data) => {
      console.info(`promise: delete data success`);
    }).catch((error: BusinessError) => {
      console.error(`promise: delete data failed, errCode : ${error.code}, errMsg : ${error.message}`);
    })
}
```
<!-- -->

### SM2
<!-- @[encrypt_and_decrypt_SM2](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/KeyUsage/EncryptionDecryption/entry/src/main/ets/pages/SM2.ets) -->

``` TypeScript
/*
 * The following uses SM2 with promise-based APIs.
 */
import { huks } from '@kit.UniversalKeystoreKit';
import { BusinessError } from '@kit.BasicServicesKit';

let sm2KeyAlias = 'test_sm2KeyAlias';
let handle: number;
let plainText = '123456';
let cipherData: Uint8Array;

function stringToUint8Array(str: string) {
  let arr: number[] = [];
  for (let i = 0, j = str.length; i < j; ++i) {
    arr.push(str.charCodeAt(i));
  }
  return new Uint8Array(arr);
}

function uint8ArrayToString(fileData: Uint8Array) {
  let dataString = '';
  for (let i = 0; i < fileData.length; i++) {
    dataString += String.fromCharCode(fileData[i]);
  }
  return dataString;
}

function getSm2GenerateProperties() {
  let properties: huks.HuksParam[] = [{
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_SM2
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_SM2_KEY_SIZE_256
  }, {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT |
    huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_DECRYPT
  }];
  return properties;
}

function getSm2EncryptProperties() {
  let properties: huks.HuksParam[] = [{
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_SM2
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_SM2_KEY_SIZE_256
  }, {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT
  }, {
    tag: huks.HuksTag.HUKS_TAG_DIGEST,
    value: huks.HuksKeyDigest.HUKS_DIGEST_SM3
  }];
  return properties;
}

function getSm2DecryptProperties() {
  let properties: huks.HuksParam[] = [{
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_SM2
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_SM2_KEY_SIZE_256
  }, {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_DECRYPT
  }, {
    tag: huks.HuksTag.HUKS_TAG_DIGEST,
    value: huks.HuksKeyDigest.HUKS_DIGEST_SM3
  }];
  return properties;
}

async function generateSm2Key() {
  /*
   * Simulate the key generation scenario.
   */
  /*
   * 1. Obtain the parameters for key generation.
   */
  let genProperties = getSm2GenerateProperties();
  let options: huks.HuksOptions = {
    properties: genProperties
  }
  /*
   * 2. Call generateKeyItem.
   */
  await huks.generateKeyItem(sm2KeyAlias, options)
    .then(() => {
      console.info(`promise: generate SM2 Key success`);
    }).catch((error: BusinessError) => {
      console.error(`promise: generate SM2 Key failed, errCode : ${error.code}, errMsg : ${error.message}`);
    })
}

async function encryptDataSm2() {
  /*
   * Simulate the encryption scenario.
   */
  /*
   * 1. Obtain the algorithm parameters for encryption.
   */
  let encryptProperties = getSm2EncryptProperties();
  let options: huks.HuksOptions = {
    properties: encryptProperties,
    inData: stringToUint8Array(plainText)
  }
  /*
   * 2. Call initSession to obtain a session handle.
   */
  await huks.initSession(sm2KeyAlias, options)
    .then((data) => {
      handle = data.handle;
    }).catch((error: BusinessError) => {
      console.error(`promise: init EncryptDataSm2 failed, errCode : ${error.code}, errMsg : ${error.message}`);
    })
  /*
   * 3. Call finishSession to obtain the ciphertext.
   */
  await huks.finishSession(handle, options)
    .then((data) => {
      console.info(`promise: encrypt data success, data is ` + uint8ArrayToString(data.outData as Uint8Array));
      cipherData = data.outData as Uint8Array;
    }).catch((error: BusinessError) => {
      console.error(`promise: encrypt data failed, errCode : ${error.code}, errMsg : ${error.message}`);
    })
}

async function decryptDataSm2() {
  /*
   * Simulate the decryption scenario.
   */
  /*
   * 1. Obtain the algorithm parameters for decryption.
   */
  let decryptOptions = getSm2DecryptProperties()
  let options: huks.HuksOptions = {
    properties: decryptOptions,
    inData: cipherData
  }
  /*
   * 2. Call initSession to obtain a session handle.
   */
  await huks.initSession(sm2KeyAlias, options)
    .then((data) => {
      handle = data.handle;
    }).catch((error: BusinessError) => {
      console.error(`promise: init DecryptDataSm2 failed, errCode : ${error.code}, errMsg : ${error.message}`);
    })
  /*
   * 3. Call finishSession to obtain the decrypted data.
   */
  await huks.finishSession(handle, options)
    .then((data) => {
      console.info(`promise: decrypt data success, data is ` + uint8ArrayToString(data.outData as Uint8Array));
    }).catch((error: BusinessError) => {
      console.error(`promise: decrypt data failed, errCode : ${error.code}, errMsg : ${error.message}`);
    })
}

async function deleteKey() {
  /*
   * Simulate the key deletion scenario.
   */
  let emptyOptions: huks.HuksOptions = {
    properties: []
  }
  /*
   * 1. Call deleteKeyItem to delete the key.
   */
  await huks.deleteKeyItem(sm2KeyAlias, emptyOptions)
    .then(() => {
      console.info(`promise: delete data success`);
    }).catch((error: BusinessError) => {
      console.error(`promise: delete data failed, errCode : ${error.code}, errMsg : ${error.message}`);
    })
}
```


<!--Del-->
### DES/CBC/NoPadding
<!-- @[encrypt_and_decrypt_DESCBCNoPadding](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/KeyUsage/EncryptionDecryption/entry/src/main/ets/pages/DESCBCNoPadding.ets) -->

``` TypeScript
/*
 * The following uses DES/CBC/NoPadding with promise-based APIs as an example.
 */
import { huks } from '@kit.UniversalKeystoreKit';
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { BusinessError } from '@kit.BasicServicesKit';

let desKeyAlias = 'test_desKeyAlias';
let handle: number;
let plainText = '12345678';
let IV = cryptoFramework.createRandom().generateRandomSync(8).data
let cipherData: Uint8Array;

function stringToUint8Array(str: string) {
  let arr: number[] = [];
  for (let i = 0, j = str.length; i < j; ++i) {
    arr.push(str.charCodeAt(i));
  }
  return new Uint8Array(arr);
}

function uint8ArrayToString(fileData: Uint8Array) {
  let dataString = '';
  for (let i = 0; i < fileData.length; i++) {
    dataString += String.fromCharCode(fileData[i]);
  }
  return dataString;
}

function getDesGenerateProperties() {
  let properties: huks.HuksParam[] = [{
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_DES
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_DES_KEY_SIZE_64
  }, {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT |
    huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_DECRYPT
  }];
  return properties;
}

function getDesEncryptProperties() {
  let properties: huks.HuksParam[] = [{
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_DES
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_DES_KEY_SIZE_64
  }, {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT
  }, {
    tag: huks.HuksTag.HUKS_TAG_PADDING,
    value: huks.HuksKeyPadding.HUKS_PADDING_NONE
  }, {
    tag: huks.HuksTag.HUKS_TAG_BLOCK_MODE,
    value: huks.HuksCipherMode.HUKS_MODE_CBC
  }, {
    tag: huks.HuksTag.HUKS_TAG_IV,
    value: IV
  }];
  return properties;
}

function getDesDecryptProperties() {
  let properties: huks.HuksParam[] = [{
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_DES
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_DES_KEY_SIZE_64
  }, {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_DECRYPT
  }, {
    tag: huks.HuksTag.HUKS_TAG_PADDING,
    value: huks.HuksKeyPadding.HUKS_PADDING_NONE
  }, {
    tag: huks.HuksTag.HUKS_TAG_BLOCK_MODE,
    value: huks.HuksCipherMode.HUKS_MODE_CBC
  }, {
    tag: huks.HuksTag.HUKS_TAG_IV,
    value: IV
  }];
  return properties;
}

async function generateDesKey() {
  /*
   * Simulate the key generation scenario.
   */
  /*
   * 1. Obtain the parameters for key generation.
   */
  let genProperties = getDesGenerateProperties();
  let options: huks.HuksOptions = {
    properties: genProperties
  }
  /*
   * 2. Call generateKeyItem.
   */
  await huks.generateKeyItem(desKeyAlias, options)
    .then(() => {
      console.info(`promise: generate DES Key success`);
    }).catch((error: BusinessError) => {
      console.error(`promise: generate DES Key failed, errCode : ${error.code}, errMsg : ${error.message}`);
    })
}

async function encryptData() {
  /*
   * Simulate the encryption scenario.
   */
  /*
   * 1. Obtain the algorithm parameters for encryption.
   */
  let encryptProperties = getDesEncryptProperties();
  let options: huks.HuksOptions = {
    properties: encryptProperties,
    inData: stringToUint8Array(plainText)
  }
  /*
   * 2. Call initSession to obtain a session handle.
   */
  await huks.initSession(desKeyAlias, options)
    .then((data) => {
      handle = data.handle;
    }).catch((error: BusinessError) => {
      console.error(`promise: init EncryptData failed, errCode : ${error.code}, errMsg : ${error.message}`);
    })
  /*
   * 3. Call finishSession to obtain the ciphertext.
   */
  await huks.finishSession(handle, options)
    .then((data) => {
      console.info(`promise: encrypt data success, data is ` + uint8ArrayToString(data.outData as Uint8Array));
      cipherData = data.outData as Uint8Array;
    }).catch((error: BusinessError) => {
      console.error(`promise: encrypt data failed, errCode : ${error.code}, errMsg : ${error.message}`);
    })
}

async function decryptData() {
  /*
   * Simulate the decryption scenario.
   */
  /*
   * 1. Obtain the algorithm parameters for decryption.
   */
  let decryptOptions = getDesDecryptProperties()
  let options: huks.HuksOptions = {
    properties: decryptOptions,
    inData: cipherData
  }
  /*
   * 2. Call initSession to obtain a session handle.
   */
  await huks.initSession(desKeyAlias, options)
    .then((data) => {
      handle = data.handle;
    }).catch((error: BusinessError) => {
      console.error(`promise: init DecryptData failed, errCode : ${error.code}, errMsg : ${error.message}`);
    })
  /*
   * 3. Call finishSession to obtain the decrypted data.
   */
  await huks.finishSession(handle, options)
    .then((data) => {
      console.info(`promise: decrypt data success, data is ` + uint8ArrayToString(data.outData as Uint8Array));
    }).catch((error: BusinessError) => {
      console.error(`promise: decrypt data failed, errCode : ${error.code}, errMsg : ${error.message}`);
    })
}

async function deleteKey() {
  /*
   * Simulate the key deletion scenario.
   */
  let emptyOptions: huks.HuksOptions = {
    properties: []
  }
  /*
   * 1. Call deleteKeyItem to delete the key.
   */
  await huks.deleteKeyItem(desKeyAlias, emptyOptions)
    .then(() => {
      console.info(`promise: delete data success`);
    }).catch((error: BusinessError) => {
      console.error(`promise: delete data failed, errCode : ${error.code}, errMsg : ${error.message}`);
    })
}
```

<!--DelEnd-->
