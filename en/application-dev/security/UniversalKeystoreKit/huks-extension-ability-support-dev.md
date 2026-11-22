# CryptoExtensionAbility Adaptation Development

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=f20935f61bcec3c96e073d6ac9c7aefe90f36d10 translatedAt=2026-11-03T05:20:57.542Z pushedAt=2026-11-03T06:56:13.000Z nl=1 -->

## Constraints

For details about the call restrictions of the CryptoExtensionAbility APIs, see [Constraints](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#constraints) in the API reference.

## How to Adapt

This document aims to guide **key management extension application developers** on how to inherit and implement the interface capabilities in [CryptoExtensionAbility](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md), covering project setup, core implementation patterns, and reference examples for all interfaces. The implementation reference provided here allows you to implement some of the interfaces as needed for your business, while other implementations call the underlying driver functions encapsulated by the driver in sequence according to business requirements.

To manually create a **CryptoExtensionAbility** component in the DevEco Studio project, perform the following steps:

1. In the **ets** directory of the target module, right-click and choose **New** > **Directory** to create a directory named **cryptoability**.

2. In the **cryptoability** directory, right-click and choose **New** > **ArkTS File** to create a file named **CryptoAbility.ets**.

   The directory structure is as follows:

   ```txt
   ├── ets
   │   └── cryptoability
   │       └── CryptoAbility.ets
   ```

3. To develop CryptoExtensionAbility, configure the [ohos.permission.CRYPTO_EXTENSION_REGISTER](../AccessToken/restricted-permissions.md#ohospermissioncrypto_extension_register) permission. This permission is one of the [restricted permissions](../AccessToken/restricted-permissions.md). Apply for it as instructed in [Requesting Restricted Permissions](../AccessToken/declare-permissions-in-acl.md).

   ```json5
   // entry/src/main/module.json5
   {
     "module": {
       // ...
       "requestPermissions": [
         {
           "name": "ohos.permission.CRYPTO_EXTENSION_REGISTER"
         }
       ],
     }
   }
   ```

4. In the module.json5 configuration file corresponding to the project module, register the CryptoExtensionAbility component under the [extensionAbilities](../../../application-dev/quick-start/module-configuration-file.md#extensionabilities) tag.

   - The name tag indicates the ability name, with a maximum length of 127 bytes. When multiple abilities are configured, each name tag must be unique.
   - The srcEntry tag indicates the code path corresponding to the current CryptoExtensionAbility component.
   - The type tag must be set to "crypto".
   - Setting the exported tag to false indicates that third-party applications are not allowed to call it.

   ```json5
   // entry/src/main/module.json5
   {
     "module": {
       // ...
       "extensionAbilities": [
           {
             "name": "CryptoExtension",
             "srcEntry": "./ets/cryptoability/CryptoAbility.ets",
             "type": "crypto",
             "exported": false
           }
       ],
     }
   }
   ```

5. In the CryptoAbility.ets file, import the dependency packages, define a custom class that inherits the [CryptoExtensionAbility](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md) component, and implement the interface functions as needed. The implementation reference provided here corresponds to the underlying driver calls as described below.

   ```ts
   import { huks, huksExternalCrypto, CryptoExtensionAbility, HuksCryptoExtensionCertInfo, HuksCryptoExtensionResult, HuksCryptoExtensionResultCode } from '@kit.UniversalKeystoreKit';
   import { util } from '@kit.ArkTS';
   import { cryptoFramework } from '@kit.CryptoArchitectureKit';
   import { deviceInfo } from '@kit.BasicServicesKit';

   export class CryptoExtension extends CryptoExtensionAbility {
     // Suggested state management mechanism, for reference only
     // 1. Handle mapping table: key = "${uid}:${handle}", value = underlying UKey handle
     private handleMap: Map<string, YourDriverHandle> = new Map();

     // 2. Session state table: key = "${uid}:${sessionHandle}", value = session intermediate data
     private sessionMap: Map<string, SessionState> = new Map();

     // 3. PIN authentication state table: key = "${uid}:${ukeyApplicationId}", value = authState
     private authStateMap: Map<string, number> = new Map();

     // 4. PIN decryption private key (generated in onGetProperty, used in onAuthUkeyPin)
     private pinDecryptKey: cryptoFramework.PriKey | null = null;
     private pinDecryptAlgo: string = '';               // Corresponding decryption algorithm
     private pinDecryptTransformation: string = '';     // Corresponding padding mode

     // 5. Handle generation counter
     private handleCounter: number = 0;

     // Extract the UID from params of the Array type
     private extractUid(params: Array<huksExternalCrypto.HuksExternalCryptoParam> | HuksCryptoExtensionParam[]): string | undefined {
       const arr = params as Array<huksExternalCrypto.HuksExternalCryptoParam>;
       const param = arr.find(p =>
         p.tag === huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_UID
       );
       return param?.value?.toString();
     }

     // Extract the UID from params of the huks.HuksOptions/HuksCryptoExtensionParams type
     private extractUidFromSessionParams(params: huks.HuksOptions | HuksCryptoExtensionParams): string | undefined {
       const props = (params as huks.HuksOptions).properties as Array<huksExternalCrypto.HuksExternalCryptoParam> | undefined;
       if (!props) return undefined;
       const param = props.find(p =>
         p.tag === huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_UID
       );
       return param?.value?.toString();
     }

     // Construct the isolation key
     private makeStorageKey(uid: string, ...parts: string[]): string {
       return [uid, ...parts].join(':');
     }

     // Generate a unique handle
     private generateUniqueHandle(): string {
       this.handleCounter += 1;
       return `handle-${this.handleCounter}-${Date.now()}`;
     }

     // Unified error return helper
     private failResult(result: HuksCryptoExtensionResult, code: number, error?: unknown): HuksCryptoExtensionResult {
       result.resultCode = code;
       if (error !== undefined) {
         result.errInfo = {
           errno: (error as UKeyDriverError)?.driverCode ?? -1,
           errorDesc: String(error)
         };
       }
       return result;
     }

     // The APIs in this step must be implemented in the class. For ease of understanding and use, each API is described in detail below.
   }
   ```

## Development Cases

### Calling onOpenResource to Open a Resource

onOpenResource is used to open a specified resource (for example, establishing a session or connection), where handle is the resource handle. When the call succeeds, the resultCode member in the return value must be set to 0, and the handle member is not empty; on call failure, resultCode carries error code information.

   ```ts
   onOpenResource(resourceId: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
     const result: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
     };

     const uid = this.extractUid(params);
     if (uid === undefined) {
       return Promise.resolve(result);
     }

     // Parse the resource index. API version 22 requires parsing the index field, and it can be used directly in API version 26.0.0 and later.
     const apiVersion = deviceInfo.sdkApiVersion;
     let index: string;
     if (apiVersion >= 26) {
       index = resourceId;
     } else {
       try {
        index = JSON.parse(resourceId)['index'];
       } catch (e) {
        result.resultCode = HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL;
        return Promise.resolve(result);
       }
     }

     let driverHandle: YourDriverHandle | null = null;
     try {
       const driverRes = YourDriverInstance.YourDriver_onOpenResource(index);
       if (driverRes.resultCode !== 0 || driverRes.driverHandle === undefined) {
        result.resultCode = driverRes.resultCode;
        if (driverRes.errInfo) result.errInfo = driverRes.errInfo;
        return Promise.resolve(result);
       }
       driverHandle = driverRes.driverHandle;

       const handle = this.generateUniqueHandle();
       const key = this.makeStorageKey(uid, handle);
       this.handleMap.set(key, driverHandle);

       result.resultCode = 0;
       result.handle = handle;
     } catch (error) {
       // Key point: the driver has allocated a handle but a subsequent failure occurs, so it must be closed proactively.
       if (driverHandle !== null) {
        try { YourDriverInstance.YourDriver_onCloseResource(driverHandle); } catch (_) {}
       }
       this.failResult(result, HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_UKEY_DRIVER_FAIL, error);
       console.error('promise: onOpenResource failed.');
     }
     return Promise.resolve(result);
   }
   ```

### Calling onCloseResource to Close a Resource

onCloseResource is used to close a specified resource (for example, releasing a session or connection), where handle is the resource handle of the resource to be closed. When the call succeeds, the resultCode member in the return value must be set to 0; on call failure, resultCode carries error code information.

   ```ts
   onCloseResource(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> | HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult> {
     const result: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
     };
  
     const uid = this.extractUid(params);
     if (uid === undefined) {
       return Promise.resolve(result);
     }
     
     // Find the internal mapping handle of the UKey.
     const key = this.makeStorageKey(uid, handle);
     const driverHandle = this.handleMap.get(key);
     if (driverHandle === undefined) {
       result.resultCode = HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_HANDLE_NOT_EXIST;
       return Promise.resolve(result);
     }

     try {
       const driverRes = YourDriverInstance.YourDriver_onCloseResource(driverHandle);
       this.handleMap.delete(key);
       result.resultCode = driverRes.resultCode;
       if (driverRes.errInfo) result.errInfo = driverRes.errInfo;
     } catch (error) {
       this.failResult(result, HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_UKEY_DRIVER_FAIL, error);
       console.error('promise: onCloseResource failed.');
     }
     return Promise.resolve(result);
   }
   ```

### Calling onGetProperty to Obtain Resource Information

onGetProperty is used to obtain the property information of a specified resource, where handle is the resource handle and propertyId is the identifier of the property to be obtained. When the call succeeds, the resultCode member in the return value must be set to 0, and the property member in the return value contains the property information. On call failure, resultCode carries error code information.

The function of exporting a public key must be implemented in **onGetProperty** so that the upstream services can use the PIN for encrypted transmission and complete PIN authentication. The encryption algorithms support RSA, SM2, and others. When the input parameter **propertyId** is set to **SKF_ExportPublicKey**, the returned public key information is in JSON format and contains the following four mandatory fields: **publicKey** (public key data), **algo** (algorithm type and key length), **transformation** (cryptographic operation parameter, such as the padding mode), and **size** (public key data length). For details about the implementation, see the **onGetProperty** API in the following sample code.

   ```ts
   onGetProperty(handle: string, propertyId: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> | HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult> {
     const result: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
       property: []
     };

     const uid = this.extractUid(params);
     if (uid === undefined) {
       return Promise.resolve(result);
     }
  
     // Must implement: export the public key for PIN encryption.
     if (propertyId === 'SKF_ExportPublicKey') {
       const encryptionAlgo = 'RSA1024';
       const padding = 'PKCS1';
       const transformation = `${encryptionAlgo}|${padding}`;

       // 1. Create an AsyKeyGenerator instance.
       const rsaGenerator = cryptoFramework.createAsyKeyGenerator(`${encryptionAlgo}|${padding}`);
       // 2. Use the key generator to randomly generate an asymmetric key pair and save the private key.
       const keyPair = rsaGenerator.generateKeyPairSync();
       this.pinDecryptKey = keyPair.priKey;
       this.pinDecryptAlgo = `${encryptionAlgo}|${padding}`;
       // 3. Export the public key and convert it into a JSON string.
       const pkData = Array.from(keyPair.pubKey.getEncoded().data);
       const encoder = new util.TextEncoder();
       const info = encoder.encodeInto(JSON.stringify({
         publicKey: pkData,
         algo: encryptionAlgo,
         transformation: transformation,
         size: pkData.length
       }));
       // Return the public key and encryption algorithm information used to encrypt the PIN. For details, see the public key export documentation.
       result.resultCode = 0;
       result.property = [{
         tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_EXTRA_DATA,
         value: info
       }];
       return Promise.resolve(result);
     }

      // Delegate other propertyId values to the driver for processing.
      try {
        const driverHandle = this.handleMap.get(this.makeStorageKey(uid, handle));
        if (driverHandle === undefined) {
          result.resultCode = HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_HANDLE_NOT_EXIST;
          return Promise.resolve(result);
        }
        const driverRes = YourDriverInstance.YourDriver_onGetProperty(driverHandle, propertyId);
        result.resultCode = driverRes.resultCode;
        result.property = driverRes.property;
        if (driverRes.errInfo) result.errInfo = driverRes.errInfo;
      } catch (error) {
        this.failResult(result, HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_UKEY_DRIVER_FAIL, error);
        console.error('promise: onGetProperty failed.');
      }
      return Promise.resolve(result);
   }
   ```

### Calling onAuthUkeyPin to Verify the PIN

**onAuthUkeyPin** verifies the PIN before signing with the private key. The encrypted PIN is carried by the [HUKS_EXT_CRYPTO_TAG_UKEY_PIN](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag) parameter in **param**, and must be decrypted using the private key saved in **onGetProperty**.

- **Verification success**: When the PIN verification succeeds, the **resultCode** member in the return value must be set to 0, and **authState** in the return value must be set to [HUKS_EXT_CRYPTO_PIN_AUTH_SUCCEEDED](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalpinauthstate).

- **Verification failure**: When the PIN is incorrect, **resultCode** carries the error code information, and **retryCount** in the return value is set to the remaining retry count, which decreases by 1 after each failed authentication.

- **UKey locked**: When the retry count reaches 0, **resultCode** is set to [HUKS_CRYPTO_EXTENSION_ERR_PIN_LOCKED](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#hukscryptoextensionresultcode), and **authState** is set to [HUKS_EXT_CRYPTO_PIN_LOCKED](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalpinauthstate).

   ```ts
   onAuthUkeyPin(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> | HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult> {
     const result: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
       authState: huksExternalCrypto.HuksExternalPinAuthState.HUKS_EXT_CRYPTO_PIN_NO_AUTH,
       retryCount: 0
     };

     const uid = this.extractUid(params);
     if (uid === undefined) {
       return Promise.resolve(result);
     }

     // 1. Obtain the ciphertext.
     const pinParam = params.find(p =>
       p.tag === huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_UKEY_PIN
     );
     if (pinParam === undefined) return Promise.resolve(result);
     const encryptedPin = pinParam.value as Uint8Array;

     // 2. Decrypt using the private key saved in onGetProperty.
     if (this.pinDecryptKey === null) {
       result.resultCode = HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_PIN_NO_AUTH;
       return Promise.resolve(result);
     }
     let plainPin: string;
     try {
       const cipher = cryptoFramework.createCipher(this.pinDecryptAlgo);
       cipher.init(cryptoFramework.CryptoMode.DECRYPT_MODE, this.pinDecryptKey, null);
       const plainBytes = cipher.doFinal(encryptedPin);
       plainPin = new util.TextDecoder().decodeToString(plainBytes);
     } catch (error) {
       result.resultCode = HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL;
       return Promise.resolve(result);
     }

     // 3. Call the driver for verification.
     const driverHandle = this.handleMap.get(this.makeStorageKey(uid, handle));
     if (driverHandle === undefined) {
       result.resultCode = HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_HANDLE_NOT_EXIST;
       return Promise.resolve(result);
     }
     try {
       const driverRes = YourDriverInstance.YourDriver_onAuthUkeyPin(driverHandle, plainPin);
       result.resultCode = driverRes.resultCode;
       result.retryCount = driverRes.retryCount;
       if (driverRes.errInfo) result.errInfo = driverRes.errInfo;

       if (driverRes.resultCode === 0) {
         // Authentication succeeds. Maintain the authentication status.
         const authKey = this.makeStorageKey(uid, 'Application-' + handle);
         this.authStateMap.set(authKey, huksExternalCrypto.HuksExternalPinAuthState.HUKS_EXT_CRYPTO_PIN_AUTH_SUCCEEDED);
         result.authState = huksExternalCrypto.HuksExternalPinAuthState.HUKS_EXT_CRYPTO_PIN_AUTH_SUCCEEDED;
       } else if (driverRes.retryCount === 0) {
         result.resultCode = HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_PIN_LOCKED;
         result.authState = huksExternalCrypto.HuksExternalPinAuthState.HUKS_EXT_CRYPTO_PIN_LOCKED;
       } else {
         result.resultCode = HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_PIN_INCORRECT;
       }
     } catch (error) {
       this.failResult(result, HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_UKEY_DRIVER_FAIL, error);
     }
     return Promise.resolve(result);
   }
   ```

### Calling onGetUkeyPinAuthState to Query the PIN Authentication State

**onGetUkeyPinAuthState** is used to query the PIN authentication state. When the call succeeds, the **resultCode** member in the return value must be set to **0**, and the **authState** member in the return value is set to the corresponding authentication state. On call failure, **resultCode** carries the error code information.

   ```ts
   onGetUkeyPinAuthState(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> | HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult> {
    const result: HuksCryptoExtensionResult = {
      resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
      authState: huksExternalCrypto.HuksExternalPinAuthState.HUKS_EXT_CRYPTO_PIN_NO_AUTH
    };
  
    const uid = this.extractUid(params);
    if (uid === undefined) {
      return Promise.resolve(result);
    }
    
    // Obtain the authentication status from the cache, or call the Driver interface to obtain the status in real time and update the cache.
    const authKey = this.makeStorageKey(uid, 'Application-' + handle);
    result.authState = this.authStateMap.get(authKey) ?? huksExternalCrypto.HuksExternalPinAuthState.HUKS_EXT_CRYPTO_PIN_NO_AUTH;
    result.resultCode = 0;
    return Promise.resolve(result);
   }
   ```

### Calling onClearUkeyPinAuthState to Reset the PIN State

**onClearUkeyPinAuthState** resets the PIN authentication state. If the call succeeds, the **resultCode** member in the return value must be set to **0**. If the call fails, **resultCode** carries the error code.

   ```ts
   onClearUkeyPinAuthState(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam> | HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult> {
    const result: HuksCryptoExtensionResult = {
      resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
    };

    const uid = this.extractUid(params);
    if (uid === undefined) {
      return Promise.resolve(result);
    }

    // Clear the authentication status in the cache, or call the Driver interface to clear the status and update the cache
    const authKey = this.makeStorageKey(uid, 'Application-' + handle);
    this.authStateMap.delete(authKey);
    result.resultCode = 0;
    return Promise.resolve(result);
   }
   ```

### Calling onInitSession to Initialize a Key Session

onInitSession is used to initialize a key session. When the call succeeds, the resultCode member in the return value must be set to 0, and the handle member is not empty. On call failure, resultCode carries error code information.

   ```ts
   onInitSession(handle: string, params: huks.HuksOptions | HuksCryptoExtensionParams): Promise<HuksCryptoExtensionResult> {
     const result: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
       handle: ""
     };

     const uid = this.extractUidFromSessionParams(params);
     if (uid === undefined) {
       return Promise.resolve(result);
     }

     const driverHandle = this.handleMap.get(this.makeStorageKey(uid, handle));
     if (driverHandle === undefined) {
       result.resultCode = HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_HANDLE_NOT_EXIST;
       return Promise.resolve(result);
     }

     let driverSession: YourDriverSessionHandle | null = null;
     let sessionHandle = '';
     try {
       const initRes: YourDriverSessionResult = YourDriverInstance.YourDriver_onInitSession(driverHandle, params) as YourDriverSessionResult;
       if (initRes.resultCode !== 0) {
         result.resultCode = initRes.resultCode;
         if (initRes.errInfo) result.errInfo = initRes.errInfo;
         return Promise.resolve(result);
       }
       driverSession = initRes.driverSession;
       sessionHandle = initRes.sessionHandle;
     } catch (error) {
       return Promise.resolve(this.failResult(result, HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_UKEY_DRIVER_FAIL, error));
     }

     // Cache on success, roll back the driver side on failure.
     try {
       const sessionKey = this.makeStorageKey(uid, sessionHandle);
       const state: SessionState = {
         driverSession: driverSession,
         accumData: new Uint8Array(),
       };
       this.sessionMap.set(sessionKey, state);
       result.resultCode = 0;
       result.handle = sessionHandle;
     } catch (error) {
       // Cache failure, roll back the driver-side session.
       if (driverSession !== null) {
         try { YourDriverInstance.YourDriver_onFinishSession(driverSession); } catch (_) {}
       }
       this.failResult(result, HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL, error);
     }
     return Promise.resolve(result);
   }
   ```

### Calling onUpdateSession to Transfer Data in Segments

onUpdateSession is used to transfer large amounts of data in segments. When the call succeeds, the resultCode member in the return value must be set to 0. On call failure, resultCode carries error code information.

   ```ts
   onUpdateSession(initHandle: string, params: huks.HuksOptions | HuksCryptoExtensionParams): Promise<HuksCryptoExtensionResult> {
     const result: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
       outData: new Uint8Array()
     };

     const uid = this.extractUidFromSessionParams(params);
     if (uid === undefined) {
       return Promise.resolve(result);
     }

     const sessionKey = this.makeStorageKey(uid, initHandle);
     const session = this.sessionMap.get(sessionKey);
     if (session === undefined) {
       result.resultCode = HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_HANDLE_NOT_EXIST;
       return Promise.resolve(result);
     }

     try {
       const driverRes: YourDriverUpdateResult = YourDriverInstance.YourDriver_onUpdateSession(session.driverSession, params);
       result.resultCode = driverRes.resultCode;
       result.outData = driverRes.outData;
       if (driverRes.errInfo) result.errInfo = driverRes.errInfo;
     } catch (error) {
       this.failResult(result, HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_UKEY_DRIVER_FAIL, error);
     }
     return Promise.resolve(result);
   }
   ```

### Calling onFinishSession to Complete Data Transfer

onFinishSession is used to transfer the last segment of plaintext, and in signature verification operations, to transfer the signature. When the call succeeds, the resultCode member in the return value must be set to 0. On call failure, resultCode carries error code information.

   ```ts
   onFinishSession(initHandle: string, params: huks.HuksOptions | HuksCryptoExtensionParams): Promise<HuksCryptoExtensionResult> {
     const result: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
       outData: new Uint8Array()
     };

     const uid = this.extractUidFromSessionParams(params);
     if (uid === undefined) {
       return Promise.resolve(result);
     }

     const sessionKey = this.makeStorageKey(uid, initHandle);
     const session = this.sessionMap.get(sessionKey);
     if (session === undefined) {
       result.resultCode = HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_HANDLE_NOT_EXIST;
       return Promise.resolve(result);
     }

     try {
       const driverRes: YourDriverFinishResult = YourDriverInstance.YourDriver_onFinishSession(session.driverSession, params);
       result.resultCode = driverRes.resultCode;
       result.outData = driverRes.outData;
       if (driverRes.errInfo) result.errInfo = driverRes.errInfo;
     } catch (error) {
       this.failResult(result, HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_UKEY_DRIVER_FAIL, error);
     } finally {
       // Clear the session cache regardless of success or failure.
       this.sessionMap.delete(sessionKey);
     }
     return Promise.resolve(result);
   }
   ```

### Calling onExportCertificate to Query a Certificate

onExportCertificate is used to query the certificate under a certain resourceId. You can obtain the certificate type expected by the service by parsing the parameter [HUKS_EXT_CRYPTO_TAG_PURPOSE](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag). If not specified, the key management extension application implementer must set a default type (a signing certificate is recommended).

   ```ts
   onExportCertificate(resourceId: string, params?: Array<huksExternalCrypto.HuksExternalCryptoParam> | HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult> {
    const result: HuksCryptoExtensionResult = {
      resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
      certs: []
    };

    const paramList = params ?? [];
    // It is recommended that 0 be the default purpose. For details, see the CryptoExtensionAbility extension capability introduction document.
    const purpose = (paramList as Array<huksExternalCrypto.HuksExternalCryptoParam>).find(p => 
      p.tag === huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_PURPOSE
    )?.value as number ?? 0;

    try {
      const driverRes: YourDriverExportCertResult = YourDriverInstance.YourDriver_onExportCertificate(resourceId, purpose);
      result.resultCode = driverRes.resultCode;
      result.certs = driverRes.certs;
      if (driverRes.errInfo) result.errInfo = driverRes.errInfo;
    } catch (error) {
      this.failResult(result, HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_UKEY_DRIVER_FAIL, error);
    }
    return Promise.resolve(result);
   }
   ```

### Calling onEnumCertificates to Query the Certificate List

onEnumCertificates is used to enumerate the certificate list. When the call succeeds, the resultCode member in the return value must be set to 0, and the certs member in the return value contains the certificate list (type Array<[HuksCryptoExtensionCertInfo](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#hukscryptoextensioncertinfo)>). On call failure, resultCode carries error code information.

   ```ts
   onEnumCertificates(params?: Array<huksExternalCrypto.HuksExternalCryptoParam> | HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult> {
    let result: HuksCryptoExtensionResult = {
      resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
      certs: []
    };

    const paramList = params ?? [];
    // It is recommended that 0 be the default purpose. For details, see the CryptoExtensionAbility extension capability introduction document.
    const purpose = (paramList as Array<huksExternalCrypto.HuksExternalCryptoParam>).find(p => 
      p.tag === huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_PURPOSE
    )?.value as number ?? 0;

    try {
      const driverRes: YourDriverEnumCertResult = YourDriverInstance.YourDriver_onEnumCertificates(purpose);
      result.resultCode = driverRes.resultCode;
      result.certs = driverRes.certs;
      if (driverRes.errInfo) result.errInfo = driverRes.errInfo;
    } catch (error) {
      this.failResult(result, HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_UKEY_DRIVER_FAIL, error);
    }
    return Promise.resolve(result);
   }
   ```

### Calling onImportCertificate to Import a Certificate

Starting from API version 26.0.0, **onImportCertificate** imports a certificate to the key management extension service. **certInfo** contains the certificate information to import, including the certificate purpose, resource ID, and certificate data. If the call succeeds, the **resultCode** member in the return value is set to **0**. If the call fails, **resultCode** carries the error code information.

   ```ts
   onImportCertificate(handle: string, params: HuksCryptoExtensionParam[], certInfo: HuksCryptoExtensionCertInfo): Promise<HuksCryptoExtensionResult> {
     const result: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
     };

     const uid = this.extractUid(params);
     if (uid === undefined) {
       return Promise.resolve(result);
     }

     const driverHandle = this.handleMap.get(this.makeStorageKey(uid, handle));
     if (driverHandle === undefined) {
       result.resultCode = HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_HANDLE_NOT_EXIST;
       return Promise.resolve(result);
     }

     try {
       const driverRes: YourDriverResult = YourDriverInstance.YourDriver_onImportCertificate(driverHandle, params, certInfo);
       result.resultCode = driverRes.resultCode;
       if (driverRes.errInfo) result.errInfo = driverRes.errInfo;
     } catch (error) {
       this.failResult(result, HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_UKEY_DRIVER_FAIL, error);
     }
     return Promise.resolve(result);
   }
   ```

### Calling onSetProperty to Set a Property

Starting from API version 26.0.0, onSetProperty performs the property setting operation. handle is the resource handle, and propertyId is the identifier of the property to set. The operation parameters are passed in params. When the call succeeds, the resultCode member in the return value must be set to 0, indicating that the property is set successfully. On call failure, resultCode carries the error code information.

   ```ts
   onSetProperty(handle: string, propertyId: string, params: HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult> {
    let result: HuksCryptoExtensionResult = {
      resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
    };

    const uid = this.extractUid(params);
    if (uid === undefined) {
      return Promise.resolve(result);
    }

     try {
       const driverHandle = this.handleMap.get(this.makeStorageKey(uid, handle));
       if (driverHandle === undefined) {
         result.resultCode = HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_HANDLE_NOT_EXIST;
         return Promise.resolve(result);
       }
       const driverRes = YourDriverInstance.YourDriver_onSetProperty(driverHandle, propertyId, params);
       result.resultCode = driverRes.resultCode;
       if (driverRes.errInfo) result.errInfo = driverRes.errInfo;
     } catch (error) {
       this.failResult(result, HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_UKEY_DRIVER_FAIL, error);
       console.error('promise: onSetProperty failed.');
     }
     return Promise.resolve(result);
   }
   ```

### Calling onGetResourceId to Obtain the Resource ID

Starting from API version 26.0.0, onGetResourceId is used to obtain the resource ID of the key extension capability. When the call succeeds, the resultCode member in the return value must be set to 0, and the resourceId member is not empty. On call failure, resultCode carries error code information.

   ```ts
   onGetResourceId(params: HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult> {
     const result: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
     };

     // Parse the required parameter.
     const resourceInfo = (params as Array<huksExternalCrypto.HuksExternalCryptoParam>).find(p => 
       p.tag === huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_RESOURCE_INFO
     )?.value as Uint8Array;
     const abilityName = (params as Array<huksExternalCrypto.HuksExternalCryptoParam>).find(p => 
       p.tag === huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_ABILITY_NAME
     )?.value.toString();
     const bundleName = (params as Array<huksExternalCrypto.HuksExternalCryptoParam>).find(p => 
       p.tag === huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_BUNDLE_NAME
     )?.value.toString();

     if (resourceInfo === undefined || abilityName === undefined || bundleName === undefined) {
       return Promise.resolve(result);
     }

     try {
       const driverRes: YourDriverGetResourceIdResult = YourDriverInstance.YourDriver_onGetResourceId(abilityName, bundleName, resourceInfo);
       result.resultCode = driverRes.resultCode;
       result.resourceId = driverRes.resourceId;
       if (driverRes.errInfo) result.errInfo = driverRes.errInfo;
     } catch (error) {
       this.failResult(result, HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL, error);
     }
     return Promise.resolve(result);
   }
   ```

### Calling onGenerateKeyItem to Generate a Key

Starting from API version 26.0.0, **onGenerateKeyItem** generates a key pair in the key management extension service. The parameters in **params** are optional and their supported range is defined by the key management extension application implementer. If the corresponding parameters are not passed in, the key management extension application implementer must set the default behavior. When the call succeeds, the **resultCode** member in the return value must be set to **0**. On call failure, **resultCode** carries the error code information.

   ```ts
   onGenerateKeyItem(handle: string, params: HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult> {
    const result: HuksCryptoExtensionResult = {
      resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
    };

    const uid = this.extractUid(params);
    if (uid === undefined) {
      return Promise.resolve(result);
    }

    const driverHandle = this.handleMap.get(this.makeStorageKey(uid, handle));
    if (driverHandle === undefined) {
      result.resultCode = HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_HANDLE_NOT_EXIST;
      return Promise.resolve(result);
    }

    // Parse the parameters; if no parameter is passed in, the driver application should set default values.
    const algorithm = (params.find(p => p.tag === huks.HuksTag.HUKS_TAG_ALGORITHM)?.value 
      as huks.HuksKeyAlg) ?? huks.HuksKeyAlg.HUKS_ALG_RSA;
    const keySize = (params.find(p => p.tag === huks.HuksTag.HUKS_TAG_KEY_SIZE)?.value 
      as huks.HuksKeySize) ?? huks.HuksKeySize.HUKS_RSA_KEY_SIZE_2048;
    const purpose = (params.find(p => p.tag === huks.HuksTag.HUKS_TAG_PURPOSE)?.value 
      as huks.HuksKeyPurpose) ?? huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_SIGN;

    try {
      const driverRes: YourDriverResult = YourDriverInstance.YourDriver_onGenerateKeyItem(driverHandle, algorithm, keySize, purpose);
      result.resultCode = driverRes.resultCode;
      if (driverRes.errInfo) result.errInfo = driverRes.errInfo;
    } catch (error) {
      this.failResult(result, HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_UKEY_DRIVER_FAIL, error);
    }
    return Promise.resolve(result);
   }
   ```

### Calling onExportKeyItem to Export a Public Key

Starting from API version 26.0.0, onExportKeyItem is used to export the public key of a specified key. The parameters in params are optional, and the supported scope is defined by the key management extension application. If the corresponding parameter is not passed in, the key management extension application implementer must set default behavior. It is recommended to pass in the key purpose (HUKS_TAG_PURPOSE) parameter so that the public key for the specified purpose can be exported. When the call succeeds, the resultCode member in the return value must be set to 0, and outData carries the exported public key data; on call failure, resultCode carries error code information.

   ```ts
   onExportKeyItem(handle: string, params: HuksCryptoExtensionParam[]): Promise<HuksCryptoExtensionResult> {
    const result: HuksCryptoExtensionResult = {
      resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
      outData: new Uint8Array()
    };

    const uid = this.extractUid(params);
    if (uid === undefined) {
      return Promise.resolve(result);
    }

    const driverHandle = this.handleMap.get(this.makeStorageKey(uid, handle));
    if (driverHandle === undefined) {
      result.resultCode = HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_HANDLE_NOT_EXIST;
      return Promise.resolve(result);
    }

    // Recommended to use the HUKS_TAG_PURPOSE parameter.
    const purpose = (params.find(p => p.tag === huks.HuksTag.HUKS_TAG_PURPOSE)?.value 
      as huks.HuksKeyPurpose) ?? huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_SIGN;

    try {
      const driverRes: YourDriverExportKeyResult = YourDriverInstance.YourDriver_onExportKeyItem(driverHandle, purpose);
      result.resultCode = driverRes.resultCode;
      result.outData = driverRes.pubKey;
      if (driverRes.errInfo) result.errInfo = driverRes.errInfo;
    } catch (error) {
      this.failResult(result, HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_UKEY_DRIVER_FAIL, error);
    }
    return Promise.resolve(result);
   }
   ```

### Calling onImportWrappedKeyItem to Import a Key Pair

Starting from API version 26.0.0, **onImportWrappedKeyItem** imports an encrypted and wrapped key pair. The parameters in **params** are optional, and their supported range is defined by the key management extension application implementer. If the corresponding parameters are not passed, the key management extension application implementer must set the default behavior. **wrappedHandle** specifies the key resource handle used to unwrap the key, and **wrappedKey** is the wrapped key data. When the call succeeds, the **resultCode** member in the return value must be set to **0**. When the call fails, **resultCode** carries the error code information.

   ```ts
   onImportWrappedKeyItem(handle: string, wrappingHandle: string, params: HuksCryptoExtensionParam[], wrappedKey: Uint8Array): Promise<HuksCryptoExtensionResult> {
    const result: HuksCryptoExtensionResult = {
      resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
    };

    const uid = this.extractUid(params);
    if (uid === undefined) {
      return Promise.resolve(result);
    }

    const driverHandle = this.handleMap.get(this.makeStorageKey(uid, handle));
    if (driverHandle === undefined) {
      result.resultCode = HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_HANDLE_NOT_EXIST;
      return Promise.resolve(result);
    }

    // Parse the parameters; if not passed in, the driver application should set default values.
    const algorithm = (params.find(p => p.tag === huks.HuksTag.HUKS_TAG_ALGORITHM)?.value 
      as huks.HuksKeyAlg) ?? huks.HuksKeyAlg.HUKS_ALG_RSA;
    const keySize = (params.find(p => p.tag === huks.HuksTag.HUKS_TAG_KEY_SIZE)?.value 
      as huks.HuksKeySize) ?? huks.HuksKeySize.HUKS_RSA_KEY_SIZE_2048;
    const purpose = (params.find(p => p.tag === huks.HuksTag.HUKS_TAG_PURPOSE)?.value 
      as huks.HuksKeyPurpose) ?? huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT;

    try {
      const driverRes: YourDriverResult = YourDriverInstance.YourDriver_onImportWrappedKeyItem(
        driverHandle, wrappingHandle, algorithm, keySize, purpose, wrappedKey
      );
      result.resultCode = driverRes.resultCode;
      if (driverRes.errInfo) result.errInfo = driverRes.errInfo;
    } catch (e) {
      this.failResult(result, HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_UKEY_DRIVER_FAIL, e);
    }
    return Promise.resolve(result);
   }
   ```

<!--no_check-->