# Importing a Key in Plaintext (ArkTS)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

This topic describes how to import a key, using AES256, RSA2048, and X25519 keys as examples. For details about the scenarios and supported algorithm specifications, see [Supported Algorithms](huks-key-import-overview.md#supported-algorithms).

## How to Develop

1. Specify the key alias. For details about the naming rules, see [Key Generation Overview and Algorithm Specifications](huks-key-generation-overview.md).

2. Encapsulate the key property set and key material.
   - The key property set must contain [HuksKeyAlg](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukskeyalg), [HuksKeySize](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukskeysize), and [HuksKeyPurpose](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukskeypurpose).
   - The key material must comply with the [HUKS key material format](huks-concepts.md#key-material-format) and is used to fill the **inData** field of [HuksOptions](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksoptions) in Uint8Array format.

3. Use [huks.importKeyItem](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksimportkeyitem9) to import the key. 

    For details about **HuksParam** and **HuksOptions**, see [HuksParam](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksparam) and [HuksOptions](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksoptions).

### Importing an AES256 Key
```ts
/* Import an AES 256-bit key in plaintext. This example uses callback-based APIs. */
import { huks } from '@kit.UniversalKeystoreKit';
import { BusinessError } from "@kit.BasicServicesKit";

/* Key material */
let plainTextSize32 = new Uint8Array([
  0xfb, 0x8b, 0x9f, 0x12, 0xa0, 0x83, 0x19, 0xbe, 0x6a, 0x6f, 0x63, 0x2a, 0x7c, 0x86, 0xba, 0xca,
  0x64, 0x0b, 0x88, 0x96, 0xe2, 0xfa, 0x77, 0xbc, 0x71, 0xe3, 0x0f, 0x0f, 0x9e, 0x3c, 0xe5, 0xf9
]);
/* 1. Set the key alias. */
let keyAlias = 'AES256Alias_sample';

/* 2. Encapsulate the key property set and key material. */
let properties: Array<huks.HuksParam> = [{
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_AES
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_AES_KEY_SIZE_256
  }, {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT | huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_DECRYPT
  },
]
let options: huks.HuksOptions = {
  properties: properties,
  inData: plainTextSize32
};

/* 3. Import the key in plaintext. */
async function importKeyItem(keyAlias: string, huksOptions: huks.HuksOptions): Promise<boolean> {
  console.info("promise: enter importKeyItem");
  let ret: boolean = false;
  try {
    await huks.importKeyItem(keyAlias, huksOptions)
      .then(() => {
        console.info(`promise: importKeyItem success`);
        ret = true;
      }).catch((error: BusinessError) => {
        console.error(`promise: importKeyItem failed errCode : ${error.code}, errMsg : ${error.message}`);
      })
  } catch (error) {
    console.error(`promise: importKeyItem input arg invalid`);
  }
  return ret;
}

async function testImport() {
  let retImp = await importKeyItem(keyAlias, options);
  if (retImp == false) {
    console.error(`testImport failed`);
    return;
  }
  console.info(`testImport success`);
}
```
### Importing an RSA2048 Key Pair
```ts
/* Import an RSA 2048-bit key in plaintext. This example uses callback-based APIs. */
import { huks } from '@kit.UniversalKeystoreKit';
import { BusinessError } from "@kit.BasicServicesKit";

let rsa2048KeyPairMaterial = new Uint8Array([
  0x01, 0x00, 0x00, 0x00, // Key algorithm (expressed in little-endian) huks.HuksKeyAlg.HUKS_ALG_RSA = 1
  0x00, 0x08, 0x00, 0x00, // Key size (bit): 2048
  0x00, 0x01, 0x00, 0x00, // Length of modulus n (byte): 256
  0x03, 0x00, 0x00, 0x00, // Length of the public key exponent e (byte): 3
  0x00, 0x01, 0x00, 0x00, // Length of the private key exponent d (byte): 256
  // Modulus n
  0xc5, 0x35, 0x62, 0x48, 0xc4, 0x92, 0x87, 0x73, 0x0d, 0x42, 0x96, 0xfc, 0x7b, 0x11, 0x05, 0x06,
  0x0f, 0x8d, 0x66, 0xc1, 0x0e, 0xad, 0x37, 0x44, 0x92, 0x95, 0x2f, 0x6a, 0x55, 0xba, 0xec, 0x1d,
  0x54, 0x62, 0x0a, 0x4b, 0xd3, 0xc7, 0x05, 0xe4, 0x07, 0x40, 0xd9, 0xb7, 0xc2, 0x12, 0xcb, 0x9a,
  0x90, 0xad, 0xe3, 0x24, 0xe8, 0x5e, 0xa6, 0xf8, 0xd0, 0x6e, 0xbc, 0xd1, 0x69, 0x7f, 0x6b, 0xe4,
  0x2b, 0x4e, 0x1a, 0x65, 0xbb, 0x73, 0x88, 0x6b, 0x7c, 0xaf, 0x7e, 0xd0, 0x47, 0x26, 0xeb, 0xa5,
  0xbe, 0xd6, 0xe8, 0xee, 0x9c, 0xa5, 0x66, 0xa5, 0xc9, 0xd3, 0x25, 0x13, 0xc4, 0x0e, 0x6c, 0xab,
  0x50, 0xb6, 0x50, 0xc9, 0xce, 0x8f, 0x0a, 0x0b, 0xc6, 0x28, 0x69, 0xe9, 0x83, 0x69, 0xde, 0x42,
  0x56, 0x79, 0x7f, 0xde, 0x86, 0x24, 0xca, 0xfc, 0xaa, 0xc0, 0xf3, 0xf3, 0x7f, 0x92, 0x8e, 0x8a,
  0x12, 0x52, 0xfe, 0x50, 0xb1, 0x5e, 0x8c, 0x01, 0xce, 0xfc, 0x7e, 0xf2, 0x4f, 0x5f, 0x03, 0xfe,
  0xa7, 0xcd, 0xa1, 0xfc, 0x94, 0x52, 0x00, 0x8b, 0x9b, 0x7f, 0x09, 0xab, 0xa8, 0xa4, 0xf5, 0xb4,
  0xa5, 0xaa, 0xfc, 0x72, 0xeb, 0x17, 0x40, 0xa9, 0xee, 0xbe, 0x8f, 0xc2, 0xd1, 0x80, 0xc2, 0x0d,
  0x44, 0xa9, 0x59, 0x44, 0x59, 0x81, 0x3b, 0x5d, 0x4a, 0xde, 0xfb, 0xae, 0x24, 0xfc, 0xa3, 0xd9,
  0xbc, 0x57, 0x55, 0xc2, 0x26, 0xbc, 0x19, 0xa7, 0x9a, 0xc5, 0x59, 0xa3, 0xee, 0x5a, 0xef, 0x41,
  0x80, 0x7d, 0xf8, 0x5e, 0xc1, 0x1d, 0x32, 0x38, 0x41, 0x5b, 0xb6, 0x92, 0xb8, 0xb7, 0x03, 0x0d,
  0x3e, 0x59, 0x0f, 0x1c, 0xb3, 0xe1, 0x2a, 0x95, 0x1a, 0x3b, 0x50, 0x4f, 0xc4, 0x1d, 0xcf, 0x73,
  0x7c, 0x14, 0xca, 0xe3, 0x0b, 0xa7, 0xc7, 0x1a, 0x41, 0x4a, 0xee, 0xbe, 0x1f, 0x43, 0xdd, 0xf9,
  // Public key exponent e
  0x01, 0x00, 0x01,
  // Private key exponent d
  0x88, 0x4b, 0x82, 0xe7, 0xe3, 0xe3, 0x99, 0x75, 0x6c, 0x9e, 0xaf, 0x17, 0x44, 0x3e, 0xd9, 0x07,
  0xfd, 0x4b, 0xae, 0xce, 0x92, 0xc4, 0x28, 0x44, 0x5e, 0x42, 0x79, 0x08, 0xb6, 0xc3, 0x7f, 0x58,
  0x2d, 0xef, 0xac, 0x4a, 0x07, 0xcd, 0xaf, 0x46, 0x8f, 0xb4, 0xc4, 0x43, 0xf9, 0xff, 0x5f, 0x74,
  0x2d, 0xb5, 0xe0, 0x1c, 0xab, 0xf4, 0x6e, 0xd5, 0xdb, 0xc8, 0x0c, 0xfb, 0x76, 0x3c, 0x38, 0x66,
  0xf3, 0x7f, 0x01, 0x43, 0x7a, 0x30, 0x39, 0x02, 0x80, 0xa4, 0x11, 0xb3, 0x04, 0xd9, 0xe3, 0x57,
  0x23, 0xf4, 0x07, 0xfc, 0x91, 0x8a, 0xc6, 0xcc, 0xa2, 0x16, 0x29, 0xb3, 0xe5, 0x76, 0x4a, 0xa8,
  0x84, 0x19, 0xdc, 0xef, 0xfc, 0xb0, 0x63, 0x33, 0x0b, 0xfa, 0xf6, 0x68, 0x0b, 0x08, 0xea, 0x31,
  0x52, 0xee, 0x99, 0xef, 0x43, 0x2a, 0xbe, 0x97, 0xad, 0xb3, 0xb9, 0x66, 0x7a, 0xae, 0xe1, 0x8f,
  0x57, 0x86, 0xe5, 0xfe, 0x14, 0x3c, 0x81, 0xd0, 0x64, 0xf8, 0x86, 0x1a, 0x0b, 0x40, 0x58, 0xc9,
  0x33, 0x49, 0xb8, 0x99, 0xc6, 0x2e, 0x94, 0x70, 0xee, 0x09, 0x88, 0xe1, 0x5c, 0x4e, 0x6c, 0x22,
  0x72, 0xa7, 0x2a, 0x21, 0xdd, 0xd7, 0x1d, 0xfc, 0x63, 0x15, 0x0b, 0xde, 0x06, 0x9c, 0xf3, 0x28,
  0xf3, 0xac, 0x4a, 0xa8, 0xb5, 0x50, 0xca, 0x9b, 0xcc, 0x0a, 0x04, 0xfe, 0x3f, 0x98, 0x68, 0x81,
  0xac, 0x24, 0x53, 0xea, 0x1f, 0x1c, 0x6e, 0x5e, 0xca, 0xe8, 0x31, 0x0d, 0x08, 0x12, 0xf3, 0x26,
  0xf8, 0x5e, 0xeb, 0x10, 0x27, 0xae, 0xaa, 0xc3, 0xad, 0x6c, 0xc1, 0x89, 0xdb, 0x7d, 0x5a, 0x12,
  0x55, 0xad, 0x11, 0x19, 0xa1, 0xa9, 0x8f, 0x0b, 0x6d, 0x78, 0x8d, 0x1c, 0xdf, 0xe5, 0x63, 0x82,
  0x0b, 0x7d, 0x23, 0x04, 0xb4, 0x75, 0x8c, 0xed, 0x77, 0xfc, 0x1a, 0x85, 0x29, 0x11, 0xe0, 0x61,
]);

/* 1. Set the key alias. */
let keyAlias = 'RSA_sample';
/* 2. Encapsulate the key property set and key material. */
let properties: Array<huks.HuksParam> = [{
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_RSA
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_RSA_KEY_SIZE_2048
  }, {
    // This tag indicates the usage of the key after it is imported. The tag cannot be changed after the key is imported.
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT | huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_DECRYPT
  }, {
    // This tag indicates the type of the key to be imported.
    tag: huks.HuksTag.HUKS_TAG_IMPORT_KEY_TYPE,
    // The value here means to import a key pair. To import a public key, set value to HUKS_KEY_TYPE_PUBLIC_KEY.
    value: huks.HuksImportKeyType.HUKS_KEY_TYPE_KEY_PAIR
  },
]
let options: huks.HuksOptions = {
  properties: properties,
  inData: rsa2048KeyPairMaterial
};

/* 3. Import the key in plaintext. */
async function importKeyItem(keyAlias: string, huksOptions: huks.HuksOptions): Promise<boolean> {
  console.info("promise: enter importKeyItem");
  let ret: boolean = false;
  try {
    await huks.importKeyItem(keyAlias, huksOptions)
      .then(() => {
        console.info(`promise: importKeyItem success`);
        ret = true;
      }).catch((error: BusinessError) => {
        console.error(`promise: importKeyItem failed errCode : ${error.code}, errMsg : ${error.message}`);
      })
  } catch (error) {
    console.error(`promise: importKeyItem input arg invalid`);
  }
  return ret;
}

async function testImport() {
  let retImp = await importKeyItem(keyAlias, options);
  if (retImp == false) {
    console.error(`testImport failed`);
    return;
  }
  console.info(`testImport success`);
}
```
### Importing the Public Key of an X25519 Key Pair
```ts
/* Import the public key of an X25519 key pair. This example uses callback-based APIs. */
import { huks } from '@kit.UniversalKeystoreKit';
import { BusinessError } from "@kit.BasicServicesKit";

// X25519 public key data. The private key and public key in the X25519 key pair are both 32 bytes (256 bits). For details about the algorithm, see related cryptography materials.
let x25519KeyPubMaterial = new Uint8Array([
  0x30, 0x2A, 0x30, 0x05, 0x06, 0x03, 0x2B, 0x65, 0x6E, 0x03, 0x21, 0x00, 0xD2, 0x36, 0x9E, 0xCF,
  0xF0, 0x61, 0x5B, 0x73, 0xCE, 0x4F, 0xF0, 0x40, 0x2B, 0x89, 0x18, 0x3E, 0x06, 0x33, 0x60, 0xC6
]);

/* 1. Set the key alias. */
let keyAlias = 'X25519_Pub_import_sample';
/* 2. Encapsulate the key property set and key material. */
let properties: Array<huks.HuksParam> = [{
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_X25519
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_CURVE25519_KEY_SIZE_256
  }, {
    // This tag indicates the usage of the key after it is imported. The tag cannot be changed after the key is imported.
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_VERIFY
  }, {
    // This tag indicates the type of the key to be imported.
    tag: huks.HuksTag.HUKS_TAG_IMPORT_KEY_TYPE,
    // The value indicates the public key to import. If the value is HUKS_KEY_TYPE_KEY_PAIR, a key pair is to be imported.
    value: huks.HuksImportKeyType.HUKS_KEY_TYPE_PUBLIC_KEY
  },
]
let options: huks.HuksOptions = {
  properties: properties,
  inData: x25519KeyPubMaterial
};

/* 3. Import the key in plaintext. */
async function importKeyItem(keyAlias: string, huksOptions: huks.HuksOptions): Promise<boolean> {
  console.info("promise: enter importKeyItem");
  let ret: boolean = false;
  try {
    await huks.importKeyItem(keyAlias, huksOptions)
      .then(() => {
        console.info(`promise: importKeyItem success`);
        ret = true;
      }).catch((error: BusinessError) => {
        console.error(`promise: importKeyItem failed errCode : ${error.code}, errMsg : ${error.message}`);
      })
  } catch (error) {
    console.error(`promise: importKeyItem input arg invalid`);
  }
  return ret;
}

async function testImport() {
  let retImp = await importKeyItem(keyAlias, options);
  if (retImp == false) {
    console.error(`testImport failed`);
    return;
  }
  console.info(`testImport success`);
}
```
## Verification

Use [huks.isKeyItemExist](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksiskeyitemexist9) to check whether the key exists. If the key exists, the key is successfully imported.

```ts
import { huks } from '@kit.UniversalKeystoreKit';
import { BusinessError } from "@kit.BasicServicesKit";

let keyAlias = 'AES256Alias_sample';
let keyProperties: Array<huks.HuksParam> = [{
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_AES
  }
]
let huksOptions: huks.HuksOptions = {
  properties: keyProperties, // It cannot be empty.
  inData: new Uint8Array(new Array()) // It cannot be empty.
}

async function isKeyItemExist(keyAlias: string, options: huks.HuksOptions): Promise<boolean> {
  console.info(`promise: enter isKeyItemExist success`);
  let ret: boolean = false;
  try {
    await huks.isKeyItemExist(keyAlias, options)
      .then((data) => {
        console.info(`promise: isKeyItemExist success, data = ${data}`);
        ret = true;
      }).catch((error: BusinessError) => {
        console.error(`promise: isKeyItemExist success, errCode : ${error.code}, errMsg : ${error.message}`);
      })
  } catch (error) {
    console.error(`promise: isKeyItemExist input arg invalid`);
  }
  return ret;
}

async function testImportKeyExist() {
  let retExist = await isKeyItemExist(keyAlias, huksOptions);
  if (retExist == false) {
    console.error(`testImportKeyExist failed`);
    return;
  }
  console.info(`testImportKeyExist success`);
}
```
