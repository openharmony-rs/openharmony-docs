# HUKS Access Control Development

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

For details about scenarios and related concepts, see [HUKS Access Control Overview](huks-identity-authentication-overview.md).

## How to Develop

### Generating a Key

Specify the fingerprint access control type and related properties.

When a key is generated or imported, set [HuksUserAuthType](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksuserauthtype9), [HuksAuthAccessType](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksauthaccesstype9), and [HuksChallengeType](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukschallengetype9).

```ts
import { huks } from '@kit.UniversalKeystoreKit';
import { BusinessError } from "@kit.BasicServicesKit";

/*
 * Set the key alias and encapsulate the key property set.
 */
let keyAlias = 'test_sm4_key_alias';
let properties: Array<huks.HuksParam> = [{
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_SM4
  }, {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT | huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_DECRYPT
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
    // Set HuksUserAuthType to fingerprint authentication.
    tag: huks.HuksTag.HUKS_TAG_USER_AUTH_TYPE,
    value: huks.HuksUserAuthType.HUKS_USER_AUTH_TYPE_FINGERPRINT
  }, {
    // Set HuksAuthAccessType to HUKS_AUTH_ACCESS_INVALID_NEW_BIO_ENROLL, which invalidates the key when a new biometric feature (fingerprint) is enrolled.
    tag: huks.HuksTag.HUKS_TAG_KEY_AUTH_ACCESS_TYPE,
    value: huks.HuksAuthAccessType.HUKS_AUTH_ACCESS_INVALID_NEW_BIO_ENROLL
  }, {
    // Use the default challenge type.
    tag: huks.HuksTag.HUKS_TAG_CHALLENGE_TYPE,
    value: huks.HuksChallengeType.HUKS_CHALLENGE_TYPE_NORMAL
  }];

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

### Passing in the Access Token

Initiate fingerprint authentication to obtain the access token and perform data operations.
   
```ts
/*
 * The following uses a 128-bit SM4 key as an example.
 */
import { huks } from '@kit.UniversalKeystoreKit';
import { userAuth } from '@kit.UserAuthenticationKit';
import { BusinessError } from "@kit.BasicServicesKit";
import { cryptoFramework } from '@kit.CryptoArchitectureKit'

/*
 * Set the key alias and encapsulate the key property set.
 */
let IV = cryptoFramework.createRandom().generateRandomSync(16).data;
let srcKeyAlias = 'test_sm4_key_alias';
let cipherInData = 'Hks_SM4_Cipher_Test_101010101010101010110_string';
let handle: number;
let challenge: Uint8Array;
let fingerAuthToken: Uint8Array;
let finishOutData: Uint8Array;
let authType = userAuth.UserAuthType.FINGERPRINT;
let authTrustLevel = userAuth.AuthTrustLevel.ATL1;
/* Set the key generation parameter set and key encryption parameter set. */
let properties: Array<huks.HuksParam> = [{
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_SM4,
  }, {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT,
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
    tag: huks.HuksTag.HUKS_TAG_IV,
    value: IV,
  }
];
/* Encryption parameter set. */
let huksOptions: huks.HuksOptions = {
  properties: properties,
  inData: new Uint8Array(new Array())
}

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

/* Initialize the session in the HUKS and obtain the challenge value. */
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

/* Call UserIAM to start fingerprint authentication and trigger the access control process in HUKS. */
function userIAMAuthFinger(huksChallenge: Uint8Array) {
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
    auth = userAuth.getUserAuthInstance(authParam, widgetParam);
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
    console.error(`authV9 start auth failed, errCode : ${err.code}, errMsg : ${err.message}`);
  }
}

async function updateSession(handle: number, huksOptions: huks.HuksOptions, token: Uint8Array) {
  console.info(`enter promise doUpdate`);
  try {
    await huks.updateSession(handle, huksOptions, token)
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

async function finishSession(handle: number, huksOptions: huks.HuksOptions, token: Uint8Array) {
  console.info(`enter promise doFinish`);
  try {
    await huks.finishSession(handle, huksOptions, token)
      .then((data) => {
        finishOutData = data.outData as Uint8Array;
        console.info(`promise: finishSession success, data = ${Uint8ArrayToString(finishOutData)}`);
      }).catch((error: BusinessError) => {
        console.error(`promise: finishSession failed, errCode : ${error.code}, errMsg : ${error.message}`);
      })
  } catch (error) {
    console.error(`promise: finishSession input arg invalid`);
  }
}

/* Perform data operations. */
async function testSm4Cipher() {
  huksOptions.inData = StringToUint8Array(cipherInData);
  /* Pass in the access token. */
  await updateSession(handle, huksOptions, fingerAuthToken);
  /* Pass in the access token. */
  await finishSession(handle, huksOptions, fingerAuthToken);
  if (Uint8ArrayToString(finishOutData) == cipherInData) {
    console.info('test finish encrypt error ');
  } else {
    console.info('test finish encrypt success');
  }
}

async function testAuthControl() {
  /* Initialize the key session to obtain a challenge. */
  await initSession(srcKeyAlias, huksOptions);
  /* Invoke userIAM to perform user identity authentication. */
  /* Complete fingerprint authentication within 10 seconds before the timeout. */
  userIAMAuthFinger(challenge);
  setTimeout(() => {
    testSm4Cipher();
  }, 10 * 1000);
}
```
