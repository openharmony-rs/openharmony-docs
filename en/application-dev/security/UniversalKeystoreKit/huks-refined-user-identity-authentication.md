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
>
> For symmetric encryption and decryption, only the AES/CBC, AES/GCM, and SM4/CBC modes support fine-grained access control.

## How to Develop
### Key Generation and Data Encryption
<!-- @[fingerprint_access_key_generation_and_encryption](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/KeyUsage/AccessControl/entry/src/main/ets/pages/FineGrainedUserIdentityAuthentication.ets) -->

``` TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
import { userAuth } from '@kit.UserAuthenticationKit';
import { BusinessError } from '@kit.BasicServicesKit';

const KEY_ALIAS = 'test_sm4_key_alias';
const CIPHER_IN_DATA = 'Hks_SM4_Cipher_Test_101010101010101010110_string'; // Plaintext
const IV = '1234567890123456'; // Initialization vector
const AUTH_TYPE = userAuth.UserAuthType.PIN; // Authentication type: PIN
const AUTH_TRUST_LEVEL = userAuth.AuthTrustLevel.ATL1; // Authentication trust level

let sessionHandle = 0; // Session handle
let challenge: Uint8Array; // Challenge value
let authToken: Uint8Array; // Authentication token
let encryptedData: Uint8Array; // Ciphertext after encryption
let decryptedData: Uint8Array; // Plaintext after decryption

class ThrowObject {
  public isThrow: boolean = false;
}

function stringToUint8Array(str: string): Uint8Array {
  let arr: number[] = [];
  for (let i = 0, j = str.length; i < j; ++i) {
    arr.push(str.charCodeAt(i));
  }
  return new Uint8Array(arr);
}

/* Step 1: Key generation module */
const KEY_GENERATION_PROPERTIES: huks.HuksParam[] = [
  {
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_SM4,
  },
  {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT | huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_DECRYPT,
  },
  {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_SM4_KEY_SIZE_128,
  },
  {
    tag: huks.HuksTag.HUKS_TAG_BLOCK_MODE,
    value: huks.HuksCipherMode.HUKS_MODE_CBC,
  },
  {
    tag: huks.HuksTag.HUKS_TAG_PADDING,
    value: huks.HuksKeyPadding.HUKS_PADDING_NONE,
  },
  {
    tag: huks.HuksTag.HUKS_TAG_USER_AUTH_TYPE,
    value: huks.HuksUserAuthType.HUKS_USER_AUTH_TYPE_PIN
  },
  {
    tag: huks.HuksTag.HUKS_TAG_KEY_AUTH_ACCESS_TYPE,
    value: huks.HuksAuthAccessType.HUKS_AUTH_ACCESS_INVALID_CLEAR_PASSWORD
  },
  {
    tag: huks.HuksTag.HUKS_TAG_CHALLENGE_TYPE,
    value: huks.HuksChallengeType.HUKS_CHALLENGE_TYPE_NORMAL
  },
  {
    tag: huks.HuksTag.HUKS_TAG_KEY_AUTH_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_DECRYPT
  }
];

function generateKeyItem(keyAlias: string, huksOptions: huks.HuksOptions, throwObject: ThrowObject): Promise<void> {
  return new Promise<void>((resolve, reject) => {
    try {
      huks.generateKeyItem(keyAlias, huksOptions, (error, data) => {
        if (error) {
          reject(error);
        } else {
          resolve(data);
        }
      });
    } catch (error) {
      throwObject.isThrow = true;
      const err = error instanceof Error ? error : new Error(String(error));
      throw err;
    }
  });
}

/* Generate an SM4 key. */
async function step1GenerateKey(): Promise<void> {
  const generateOptions: huks.HuksOptions = {
    properties: KEY_GENERATION_PROPERTIES,
    inData: new Uint8Array([])
  };

  let throwObject: ThrowObject = { isThrow: true };
  try {
    await generateKeyItem(KEY_ALIAS, generateOptions, throwObject)
      .then((data) => {
        console.info(`Key generated successfully: ${JSON.stringify(data)}`);
      })
      .catch((error: Error) => {
        if (throwObject.isThrow) {
          const err = error instanceof Error ? error : new Error(String(error));
          throw err;
        } else {
          console.error(`Failed to generate the key: ${JSON.stringify(error)}`);
        }
      });
  } catch (error) {
    console.error(`Invalid key generation parameter: ${JSON.stringify(error)}`);
    const err = error instanceof Error ? error : new Error(String(error));
    throw err;
  }
}

/* Step 2: Encryption module */
const ENCRYPTION_PROPERTIES: huks.HuksParam[] = [
  {
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_SM4,
  },
  {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT,
  },
  {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_SM4_KEY_SIZE_128,
  },
  {
    tag: huks.HuksTag.HUKS_TAG_PADDING,
    value: huks.HuksKeyPadding.HUKS_PADDING_NONE,
  },
  {
    tag: huks.HuksTag.HUKS_TAG_BLOCK_MODE,
    value: huks.HuksCipherMode.HUKS_MODE_CBC,
  },
  {
    tag: huks.HuksTag.HUKS_TAG_IV,
    value: stringToUint8Array(IV),
  }
];

function initEncryptSession(keyAlias: string, huksOptions: huks.HuksOptions,
  throwObject: ThrowObject): Promise<huks.HuksSessionHandle> {
  return new Promise<huks.HuksSessionHandle>((resolve, reject) => {
    try {
      huks.initSession(keyAlias, huksOptions, (error, data) => {
        if (error) {
          reject(error);
        } else {
          resolve(data);
        }
      });
    } catch (error) {
      throwObject.isThrow = true;
      const err = error instanceof Error ? error : new Error(String(error));
      throw err;
    }
  });
}

function finishEncryptSession(handle: number, huksOptions: huks.HuksOptions,
  throwObject: ThrowObject): Promise<huks.HuksReturnResult> {
  return new Promise<huks.HuksReturnResult>((resolve, reject) => {
    try {
      huks.finishSession(handle, huksOptions, (error, data) => {
        if (error) {
          reject(error);
        } else {
          resolve(data);
        }
      });
    } catch (error) {
      throwObject.isThrow = true;
      const err = error instanceof Error ? error : new Error(String(error));
      throw err;
    }
  });
}

/* Encrypt data. */
async function step2EncryptData(): Promise<void> {
  const encryptOptions: huks.HuksOptions = {
    properties: ENCRYPTION_PROPERTIES,
    inData: new Uint8Array([])
  };

  /* Initialize the encryption session. */
  let throwObject: ThrowObject = { isThrow: true };
  try {
    await initEncryptSession(KEY_ALIAS, encryptOptions, throwObject)
      .then((data) => {
        console.info(`Encryption session initialized successfully: ${JSON.stringify(data)}`);
        sessionHandle = data.handle as number;
        challenge = data.challenge as Uint8Array;
      })
      .catch((error: Error) => {
        if (throwObject.isThrow) {
          const err = error instanceof Error ? error : new Error(String(error));
          throw err;
        } else {
          console.error(`Failed to initialize the encryption session: ${JSON.stringify(error)}`);
        }
      });
  } catch (error) {
    console.error(`Invalid initialization parameters for the encryption session: ${JSON.stringify(error)}`);
    const err = error instanceof Error ? error : new Error(String(error));
    throw err;
  }

  /* Execute the encryption operation. */
  encryptOptions.inData = stringToUint8Array(CIPHER_IN_DATA);
  throwObject = { isThrow: true };
  try {
    await finishEncryptSession(sessionHandle, encryptOptions, throwObject)
      .then((data) => {
        encryptedData = data.outData as Uint8Array;
        console.info(`Data encrypted successfully: ${JSON.stringify(data)}`);
      })
      .catch((error: Error) => {
        if (throwObject.isThrow) {
          const err = error instanceof Error ? error : new Error(String(error));
          throw err;
        } else {
          console.error(`Data encryption failed: ${JSON.stringify(error)}`);
        }
      });
  } catch (error) {
    console.error(`Invalid data encryption parameter: ${JSON.stringify(error)}`);
    const err = error instanceof Error ? error : new Error(String(error));
    throw err;
  }
}
```

### User Authentication
<!-- @[fingerprint_access_user_authentication](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/KeyUsage/AccessControl/entry/src/main/ets/pages/FineGrainedUserIdentityAuthentication.ets) -->

``` TypeScript
/* Step 3: User authentication module */
function performUserAuthentication(huksChallenge: Uint8Array): void {
  /* Set authentication parameters. */
  const authTypeList: userAuth.UserAuthType[] = [AUTH_TYPE];
  const authParam: userAuth.AuthParam = {
    challenge: huksChallenge,
    authType: authTypeList,
    authTrustLevel: AUTH_TRUST_LEVEL
  };

  const widgetParam: userAuth.WidgetParam = {
    title: 'PIN',
  };

  /* Obtain the authentication instance. */
  let auth: userAuth.UserAuthInstance;
  try {
    auth = userAuth.getUserAuthInstance(authParam, widgetParam);
    console.info('Authentication instance obtained successfully.');
  } catch (error) {
    console.error('Failed to obtain the authentication instance: ' + JSON.stringify(error));
    const err = error instanceof Error ? error : new Error(String(error));
    throw err;
  }

  /* Subscribe to the authentication result. */
  try {
    auth.on('result', {
      onResult(result) {
        console.info('User authentication succeeded. Token obtained: ' + JSON.stringify(result));
        authToken = result.token;
        step32CompleteDecryption();
      }
    });
    console.info('Subscription to the authentication result succeeded.');
  } catch (error) {
    console.error('Failed to subscribe to the authentication result: ' + JSON.stringify(error));
    const err = error instanceof Error ? error : new Error(String(error));
    throw err;
  }

  try {
    auth.start();
    console.info('The authentication process has been started. Waiting for the user to enter the PIN...');
  } catch (error) {
    console.error('Failed to start authentication: ' + JSON.stringify(error));
    const err = error instanceof Error ? error : new Error(String(error));
    throw err;
  }
}
```

### Data Decryption and Verification
<!-- @[fingerprint_access_decryption_and_verification](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/KeyUsage/AccessControl/entry/src/main/ets/pages/FineGrainedUserIdentityAuthentication.ets) -->

``` TypeScript
/* Step 4: Decryption module */
const DECRYPTION_PROPERTIES: huks.HuksParam[] = [
  {
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_SM4,
  },
  {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_DECRYPT,
  },
  {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_SM4_KEY_SIZE_128,
  },
  {
    tag: huks.HuksTag.HUKS_TAG_PADDING,
    value: huks.HuksKeyPadding.HUKS_PADDING_NONE,
  },
  {
    tag: huks.HuksTag.HUKS_TAG_BLOCK_MODE,
    value: huks.HuksCipherMode.HUKS_MODE_CBC,
  },
  {
    tag: huks.HuksTag.HUKS_TAG_IV,
    value: stringToUint8Array(IV),
  }
];

function initDecryptSession(keyAlias: string, huksOptions: huks.HuksOptions,
  throwObject: ThrowObject): Promise<huks.HuksSessionHandle> {
  return new Promise<huks.HuksSessionHandle>((resolve, reject) => {
    try {
      huks.initSession(keyAlias, huksOptions, (error, data) => {
        if (error) {
          reject(error);
        } else {
          resolve(data);
        }
      });
    } catch (error) {
      throwObject.isThrow = true;
      const err = error instanceof Error ? error : new Error(String(error));
      throw err;
    }
  });
}

function finishDecryptSession(handle: number, huksOptions: huks.HuksOptions, token: Uint8Array,
  throwObject: ThrowObject): Promise<huks.HuksReturnResult> {
  return new Promise<huks.HuksReturnResult>((resolve, reject) => {
    try {
      huks.finishSession(handle, huksOptions, token, (error, data) => {
        if (error) {
          reject(error);
        } else {
          resolve(data);
        }
      });
    } catch (error) {
      throwObject.isThrow = true;
      const err = error instanceof Error ? error : new Error(String(error));
      throw err;
    }
  });
}

/* Initialize the decryption session and trigger user authentication. */
async function step31DecryptionAndAuth(): Promise<void> {

  const decryptOptions: huks.HuksOptions = {
    properties: DECRYPTION_PROPERTIES,
    inData: new Uint8Array([])
  };

  /* Initialize the decryption session and obtain the challenge value. */
  let throwObject: ThrowObject = { isThrow: true };
  try {
    await initDecryptSession(KEY_ALIAS, decryptOptions, throwObject)
      .then((data) => {
        console.info(`Decryption session initialized successfully: ${JSON.stringify(data)}`);
        sessionHandle = data.handle as number;
        challenge = data.challenge as Uint8Array;
        console.info('Challenge value obtained: ' + challenge.toString());

        /* Trigger the user authentication process. */
        performUserAuthentication(challenge);
      })
      .catch((error: Error) => {
        if (throwObject.isThrow) {
          const err = error instanceof Error ? error : new Error(String(error));
          throw err;
        } else {
          console.error(`Failed to initialize the decryption session: ${JSON.stringify(error)}`);
        }
      });
  } catch (error) {
    console.error(`Invalid initialization parameters for the decryption session: ${JSON.stringify(error)}`);
    const err = error instanceof Error ? error : new Error(String(error));
    throw err;
  }
}

/* Complete the decryption. */
async function step32CompleteDecryption(): Promise<void> {
  const decryptOptions: huks.HuksOptions = {
    properties: DECRYPTION_PROPERTIES,
    inData: encryptedData // Use the previously encrypted ciphertext.
  };

  let throwObject: ThrowObject = { isThrow: true };
  try {
    await finishDecryptSession(sessionHandle, decryptOptions, authToken, throwObject)
      .then((data) => {
        decryptedData = data.outData as Uint8Array;
        console.info(`Data decrypted successfully: ${JSON.stringify(data)}`);

        /* Verify the decryption result. */
        const originalData = stringToUint8Array(CIPHER_IN_DATA);
        if (decryptedData.toString() === originalData.toString()) {
          console.info('Decryption verification succeeded. The decrypted data is the same as the source plaintext.');
        } else {
          console.error ('Decryption verification failed. The decrypted data is different from the source plaintext.');
        }
      })
      .catch((error: BusinessError) => {
        if (throwObject.isThrow) {
          const err = error instanceof Error ? error : new Error(String(error));
          throw err;
        } else {
          console.error(`Data decryption failed: ${JSON.stringify(error)}`);
        }
      });
  } catch (error) {
    console.error(`Invalid data decryption parameter: ${JSON.stringify(error)}`);
    const err = error instanceof Error ? error : new Error(String(error));
    throw err;
  }
}

/* Main function: Execute the complete SM4 encryption and decryption process. */
async function main(): Promise<void> {
    /* Step 1: Generate a key. */
    await step1GenerateKey();
    /* Step 2: Encrypt data. */
    await step2EncryptData();
    /* Step 3: Initialize decryption and perform user authentication. */
    await step31DecryptionAndAuth();
}
```
