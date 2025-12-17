# Refined Key Access Control Development

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

As an extension of the access control based on user identity authentication, the refined key access control provides fine-grained access control capabilities via secondary identity authentication based on biometric features and lock screen passwords. You can set whether identity authentication is required for a key in one or more scenarios such as encryption, decryption, signing, signature verification, key agreement, and key derivation.

For example, a service needs to use a HUKS key to encrypt the account password information. In this scenario, identity authentication is not required in encryption but required in decryption. To achieve this purpose, you can use the refined access control feature provided by HUKS.

To implement this feature, you only need to set **HuksTag** to **HUKS_TAG_KEY_AUTH_PURPOSE**.

> **NOTE**
> For symmetric encryption and decryption, only the AES/CBC, AES/GCM, and SM4/CBC modes support fine-grained access control.

## How to Develop

### Generating a Key
Set the access control type to fingerprint authentication and set other parameters including **HUKS_TAG_KEY_AUTH_PURPOSE**.
   
```ts
import { huks } from "@kit.UniversalKeystoreKit";
import { BusinessError } from "@kit.BasicServicesKit";

/*
 * Set the key alias and encapsulate the key property set.
 */
let keyAlias = 'test_sm4_key_alias';
let properties: Array<huks.HuksParam> = [{
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_SM4,
  }, {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT | huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_DECRYPT,
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_SM4_KEY_SIZE_128,
  }, {
    tag: huks.HuksTag.HUKS_TAG_BLOCK_MODE,
    value: huks.HuksCipherMode.HUKS_MODE_CBC,
  }, {
    tag: huks.HuksTag.HUKS_TAG_PADDING,
    value: huks.HuksKeyPadding.HUKS_PADDING_NONE,
  }, {
    tag: huks.HuksTag.HUKS_TAG_USER_AUTH_TYPE,
    value: huks.HuksUserAuthType.HUKS_USER_AUTH_TYPE_FINGERPRINT
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_AUTH_ACCESS_TYPE,
    value: huks.HuksAuthAccessType.HUKS_AUTH_ACCESS_INVALID_NEW_BIO_ENROLL
  }, {
    tag: huks.HuksTag.HUKS_TAG_CHALLENGE_TYPE,
    value: huks.HuksChallengeType.HUKS_CHALLENGE_TYPE_NORMAL
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_AUTH_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_DECRYPT
  }
];
let huksOptions: huks.HuksOptions = {
  properties: properties,
  inData: new Uint8Array(new Array())
}

/*
 * Generate a key.
 */
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

async function TestGenKeyForFingerprintAccessControl() {
  await generateKeyItem(keyAlias, huksOptions);
}
```

### Using a Key
The key does not need user identity authentication for encryption but requires it for decryption.
   
```ts
import { huks } from "@kit.UniversalKeystoreKit";
import { userAuth } from '@kit.UserAuthenticationKit';
import { BusinessError } from "@kit.BasicServicesKit";
import { cryptoFramework } from '@kit.CryptoArchitectureKit'

function StringToUint8Array(str: string) {
  let arr: number[] = [];
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
let keyAlias = 'test_sm4_key_alias';
let cipherInData = 'Hks_SM4_Cipher_Test_101010101010101010110_string'; // Plaintext.
let IV = cryptoFramework.createRandom().generateRandomSync(16).data;
let handle = 0;
let cipherText: Uint8Array; // Ciphertext after encryption.
let fingerAuthToken: Uint8Array;
let challenge: Uint8Array;
let authType = userAuth.UserAuthType.FINGERPRINT;
let authTrustLevel = userAuth.AuthTrustLevel.ATL1;
/* Encryption parameter set. */
let propertiesEncrypt: Array<huks.HuksParam> = [{
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_SM4,
  }, {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT,
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_SM4_KEY_SIZE_128,
  }, {
    tag: huks.HuksTag.HUKS_TAG_PADDING,
    value: huks.HuksKeyPadding.HUKS_PADDING_NONE,
  }, {
    tag: huks.HuksTag.HUKS_TAG_BLOCK_MODE,
    value: huks.HuksCipherMode.HUKS_MODE_CBC,
  }, {
    tag: huks.HuksTag.HUKS_TAG_IV,
    value: IV,
  }
];
let encryptOptions: huks.HuksOptions = {
  properties: propertiesEncrypt,
  inData: new Uint8Array(new Array())
}
/* Decryption parameter set. */
let propertiesDecrypt: Array<huks.HuksParam> = [{
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_SM4,
  }, {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_DECRYPT,
  }, {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_SM4_KEY_SIZE_128,
  }, {
    tag: huks.HuksTag.HUKS_TAG_PADDING,
    value: huks.HuksKeyPadding.HUKS_PADDING_NONE,
  }, {
    tag: huks.HuksTag.HUKS_TAG_BLOCK_MODE,
    value: huks.HuksCipherMode.HUKS_MODE_CBC,
  }, {
    tag: huks.HuksTag.HUKS_TAG_IV,
    value: IV,
  }
]
let decryptOptions: huks.HuksOptions = {
  properties: propertiesDecrypt,
  inData: new Uint8Array(new Array())
}

async function initSession(keyAlias: string, huksOptions: huks.HuksOptions) {
  console.info(`promise: enter initSession`);
  try {
    await huks.initSession(keyAlias, huksOptions)
      .then((data) => {
        handle = data.handle;
        if (data.challenge != undefined) {
          challenge = data.challenge as Uint8Array;
        }
        console.info(`promise: initSession success`);
      }).catch((error: BusinessError) => {
        console.error(`promise: initSession failed, errCode : ${error.code}, errMsg : ${error.message}`);
      })
  } catch (error) {
    console.error(`promise: initSession input arg invalid`);
  }
}

async function finishSession(handle: number, huksOptions: huks.HuksOptions, token?: Uint8Array) {
  console.info(`promise: enter finishSession`);
  try {
    await huks.finishSession(handle, huksOptions, token)
      .then((data) => {
        cipherText = data.outData as Uint8Array;
        console.info(`promise: finishSession success, data = ${Uint8ArrayToString(cipherText)}`);
      }).catch((error: BusinessError) => {
        console.error(`promise: finishSession failed, errCode : ${error.code}, errMsg : ${error.message}`);
      })
  } catch (error) {
    console.error(`promise: finishSession input arg invalid`);
  }
}

async function finishDecrypt(handle: number, huksOptions: huks.HuksOptions, token: Uint8Array) {
  await finishSession(handle, huksOptions, token)
}

async function userIAMAuthFinger(huksChallenge: Uint8Array) {
  // Obtain an authentication object.
  let authTypeList: userAuth.UserAuthType[] = [authType];
  const authParam: userAuth.AuthParam = {
    challenge: huksChallenge,
    authType: authTypeList,
    authTrustLevel: userAuth.AuthTrustLevel.ATL1
  };
  const widgetParam: userAuth.WidgetParam = {
    title: 'Enter password',
  };
  let auth: userAuth.UserAuthInstance;
  let err: BusinessError;
  try {
    auth = await userAuth.getUserAuthInstance(authParam, widgetParam)
    console.info("get auth instance success");
  } catch (error) {
    err = error as BusinessError;
    console.error(`get auth instance failed, errCode : ${err.code}, errMsg : ${err.message}`);
    return;
  }
  // Subscribe to the authentication result.
  try {
    auth.on("result", {
      onResult(result) {
        console.info(`[HUKS] -> [IAM]  userAuthInstance callback result =
          ${result.result}, ${result.token}, ${result.authType}, ${result.enrolledState}`);
        fingerAuthToken = result.token;
      }
    });
    console.info("subscribe authentication event success");
  } catch (error) {
    err = error as BusinessError;
    console.error(`subscribe authentication event failed, errCode : ${err.code}, errMsg : ${err.message}`);
  }
  // Start user authentication.
  try {
    auth.start();
    console.info("authV9 start auth success");
  } catch (error) {
    err = error as BusinessError;
    console.info(`authV9 start auth failed, errCode : ${err.code}, errMsg : ${err.message}`);
  }
}

/* 1. User identity authentication is not required when the key is used for encryption. */
async function testSm4Encrypt() {
  console.info(`enter testSm4Encrypt`);
  /* Initialize the key session to obtain a challenge. */
  await initSession(keyAlias, encryptOptions);
  /* Encryption. */
  encryptOptions.inData = StringToUint8Array(cipherInData);
  await finishSession(handle, encryptOptions);
}

/* 2. User identity authentication is required when the key is used for decryption. */
async function testSm4Decrypt() {
  console.info(`enter testSm4Decrypt`);
  /* Initialize the key session to obtain a challenge. */
  await initSession(keyAlias, decryptOptions);
  /* Invoke userIAM to perform user identity authentication. */
  userIAMAuthFinger(challenge);
  setTimeout(() => {
    /* Perform decryption after the authentication is successful. The authToken value returned after the authentication needs to be passed in. */
    /* Complete fingerprint authentication within 10 seconds before the timeout. */
    decryptOptions.inData = cipherText;
    finishDecrypt(handle, decryptOptions, fingerAuthToken);
  }, 10 * 1000)
}

async function testSm4EncryptDecrypt() {
  await testSm4Encrypt();
  await testSm4Decrypt();
}
```
