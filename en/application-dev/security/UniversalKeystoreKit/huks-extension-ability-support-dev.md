# CryptoExtensionAbility Adaptation Development Guide

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

## Adaptation Guide

This document provides the reference for driver vendors to inherit the API capabilities required for implementing [CryptoExtensionAbility](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md). Other implementations need to call the underlying driver functions encapsulated by the drivers in sequence based on service requirements.

To manually create a **CryptoExtensionAbility** component in the DevEco Studio project, perform the following steps:

1. In the **ets** directory of the target module, right-click and choose **New** > **Directory** to create a directory named **cryptoability**.

2. In the **cryptoability** directory, right-click and choose **New** > **ArkTS File** to create a file named **CryptoAbility.ets**.

   The directory structure is as follows:
   ```json5
   ├── ets
   │   └── cryptoability
   │       └── CryptoAbility.ets
   ```

3. Apply for the [ohos.permission.CRYPTO_EXTENSION_REGISTER](../AccessToken/restricted-permissions.md#ohospermissioncrypto_extension_register) permission as instructed in [Requesting Restricted Permissions](../AccessToken/declare-permissions-in-acl.md), because this permission is one of [restricted permissions](../AccessToken/restricted-permissions.md).
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

4. Register the **AppServiceExtensionAbility** component in the **module.json5** file of the target module. The **name** tag indicates the ability name, which can contain a maximum of 127 bytes. The **srcEntry** tag indicates the code path of the **CryptoExtensionAbility** component. The **type** tag must be set to **crypto**. If **exported** is set to **false**, third-party applications are not allowed to call the component. If multiple abilities are configured, each **name** tag must be unique.

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

5. In the **CryptoAbility.ets** file, add the dependency package of **CryptoExtensionAbility**, and customize the class to inherit **CryptoExtensionAbility** and implement its API functions. For importing **CryptoExtensionAbility**, all functions provided by [CryptoExtensionAbility](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md) must be implemented. The following is an implementation reference, and the corresponding relationship between the functions and the calls of the underlying drivers is as follows.
   > **NOTE**
   >
   > 1. Handle resources and PIN authentication status must be isolated based on the UID. The input parameter **params** of the **onOpenResource**, **onCloseResource**, **onAuthUkeyPin**, **onGetUkeyPinAuthState**, and **onClearUkeyPinAuthState** APIs contain the UID information of the service (the service identity can be obtained through [HUKS_EXT_CRYPTO_TAG_UID](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag)).
   > 2. The errors of the API functions cannot be returned in a customized manner. If the errors are not returned in the mode defined by the API, an exception occurs.

   ```ts
   import { huks, huksExternalCrypto, CryptoExtensionAbility, HuksCryptoExtensionCertInfo, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';
   import { util } from '@kit.ArkTS'
   import { cryptoFramework } from '@kit.CryptoArchitectureKit'

   class CryptoExtension extends CryptoExtensionAbility {
     // The APIs in this step must be implemented in the class. For ease of understanding and use, each API is described in detail below.
   }
   ```

   **API description**

   (1) **onOpenResource** opens a specified resource (for example, to establish a session or connection) during Ukey signature verification. **resourceId** indicates the ID of the resource to be opened. The application identity can be carried by the [HUKS_EXT_CRYPTO_TAG_UID](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag) parameter in **params**. If the call is successful, **resultCode** in the return value is set to **0** and **handle** is not empty. If the call fails, **resultCode** carries an error code

   ```ts
   onOpenResource(resourceId: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
     // Construct a result object. By default, the operation fails, and the return value is **HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL**.
     let result: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
     };

     // Obtain appId.
     let appId: string | undefined = params.find((param =>
       param.tag === huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_UID))?.value.toString();
     if (appId === undefined) {
       return Promise.resolve(result);
     }

     // Parse resource index.
     let index: string = JSON.parse(resourceId)['index'];

     // ...
     let res: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
     }
     try {
       let driver: YourUKeyDriver = YourDriverInstance;
       res = driver.YourDriver_onOpenResource(index, ...);
       // Scenario: The resource is opened successfully.
       result.resultCode = res.resultCode
       result.handle = res.handle
     } catch (error) {
       // Scenario: The resource fails to be opened.
       result.resultCode = res.resultCode
       console.error(`promise: onOpenResource failed`);
     }
     return Promise.resolve(result);
   }
   ```

   (2) **onCloseResource** closes a specified resource (for example, to release a session or connection) during Ukey signature verification. **handle** indicates the handle of the resource to be closed. The application identity can be carried by the [HUKS_EXT_CRYPTO_TAG_UID](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag) parameter in **params**. If the call is successful, **resultCode** in the return value is set to **0**. If the call fails, **resultCode** carries an error code.

   ```ts
   onCloseResource(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
     // ...
     let result: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
     };
     
     let res: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
     }
     try {
       let driver: YourUKeyDriver = YourDriverInstance;
       res = driver.YourDriver_closeOpenResource(handle, ...);
       // Scenario: The resource is closed successfully.
       result.resultCode = res.resultCode
     } catch (error) {
       // Scenario: The resource fails to be closed.
       result.resultCode = res.resultCode
       console.error(`promise: onCloseResource failed`);
     }
     return Promise.resolve(result);
   }
   ```

   (3) **onGetProperty** obtains the property information of a specified resource during Ukey signature verification. **handle** indicates the resource handle, and **propertyId** indicates the ID of the property to be obtained. The application identity can be carried by the [HUKS_EXT_CRYPTO_TAG_UID](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag) parameter in **params**. If the call is successful, **resultCode** is set to **0** and **property** contains the property information in the return value. If the call fails, **resultCode** carries an error code

   The function of exporting a public key must be implemented in **onGetProperty** so that the upstream services can use the PIN for encrypted transmission and complete PIN authentication. The encryption algorithms support RSA, SM2, and others. When the input parameter **propertyId** is set to **SKF_ExportPublicKey**, the returned public key information is in JSON format and contains the following four mandatory fields: **publicKey** (public key data), **algo** (algorithm type and key length), **transformation** (cryptographic operation parameter, such as the padding mode), and **size** (public key data length). For details about the implementation, see the **onGetProperty** API in the following sample code.

   ```ts
   onGetProperty(handle: string, propertyId: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
     // ...
     let emptyArray: Array<huksExternalCrypto.HuksExternalCryptoParam> = [];
     let result: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
       property: emptyArray
     };

     // Export the public key.
     if (propertyId == 'SKF_ExportPublicKey') {
       result.resultCode = 0
       let encryptionAlgo: string = 'RSA1024'
       let padding: string = 'PRIMES_2';
       // 1. Create an AsyKeyGenerator instance.
       let rsaGenerator = cryptoFramework.createAsyKeyGenerator(`${encryptionAlgo}|${padding}`);
       // 2. Use AsyKeyGenerator to randomly generate an asymmetric key pair.
       let keyPair = rsaGenerator.generateKeyPairSync();
       // 3. Export the public key and convert it into a JSON string.
       const pkData = Array.from(keyPair.pubKey.getEncoded().data);
       let transformation: string = 'RSA1024|PKCS1'
       const encoder = new util.TextEncoder();
       let info = encoder.encodeInto(JSON.stringify({
         publicKey: pkData,
         algo: encryptionAlgo,
         transformation: transformation,
         size: pkData.length
       }));
       // 4. Save the private key, which will be used to decrypt encrypted data.
       let privKey = keyPair.priKey
       // Return the public key and encryption algorithm information used for encrypted transmission of the PIN. For details, see the public key export document.
       result.property = [
         { tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_EXTRA_DATA, value: info }
       ]
       return Promise.resolve(result);
     }
  
     let res: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
     }
     try {
       // Scenario: The properties are obtained successfully.
       let driver: YourUKeyDriver = YourDriverInstance;
       res = driver.YourDriver_onGetProperty(...);
       result.resultCode = res.resultCode
       result.property = res.property
     } catch (error) {
       // Scenario: The properties fail to be obtained.
       result.resultCode = res.resultCode
       console.error(`promise: onGetProperty failed`);
     }
     return Promise.resolve(result);
   }
   ```

   (4) **onAuthUkeyPin** verifies the PIN before the Ukey signature. The encrypted PIN is carried by the [HUKS_EXT_CRYPTO_TAG_UKEY_PIN](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag) parameter in **param** and needs to be decrypted using the private key saved in **onGetProperty**.

   When the PIN verification is successful, **resultCode** is set to **0** and **authState** is set to [HUKS_EXT_CRYPTO_PIN_AUTH_SUCCEEDED](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalpinauthstate) in the return value. If the PIN is incorrect, the value of **resultCode** is an error code, and the value of **retryCount** is the number of remaining retries. The number of retries decreases by 1 each time the authentication fails. When the number of retries is **0**, the value of **resultCode** is [HUKS_CRYPTO_EXTENSION_ERR_PIN_LOCKED](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#hukscryptoextensionresultcode) and the value of **authState** is [HUKS_EXT_CRYPTO_PIN_LOCKED](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalpinauthstate).

   ```ts
   onAuthUkeyPin(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
     let pin: string | undefined = undefined;
     for (let param of params) {
       if (param.tag == huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_UKEY_PIN) {
         let originPinData = param.value as Uint8Array;
         // Decrypt originPinData based on the encryption algorithm and padding mode passed from the exported public key to obtain the PIN.
         // ...
       }
     }
     // ...
     let result: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
       authState: huksExternalCrypto.HuksExternalPinAuthState.HUKS_EXT_CRYPTO_PIN_NO_AUTH,
       retryCount: 0
     };
  
     let res: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
     }
     try {
       // Scenario: The PIN authentication is successful.
       let driver: YourUKeyDriver = YourDriverInstance;
       res = driver.YourDriver_onAuthUkeyPin(pin, ...);
       result.resultCode = res.resultCode
       result.authState = res.authState
     } catch (error) {
       // Scenario: The PIN authentication fails.
       result.resultCode = res.resultCode
       result.retryCount = res.retryCount
       console.error(`promise: onAuthUkeyPin failed`);
     }
     return Promise.resolve(result);
   }
   ```

   (5) **onGetUkeyPinAuthState** queries the PIN authentication state of the application. If the API call is successful, **resultCode** is set to **0** and **authState** is set to the corresponding authentication state in the return value. If the call fails, **resultCode** carries an error code

   ```ts
   onGetUkeyPinAuthState(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
     // ...
     let result: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
       authState: 0
     };

     let res: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
     }
     try {
       // Scenario: The PIN authentication status is successfully obtained.
       let driver: YourUKeyDriver = YourDriverInstance;
       res = driver.YourDriver_onAuthUkeyPin(...);
       result.resultCode = res.resultCode
       result.authState = res.authState
       if (result.authState != 0) {
         // Scenario: The PIN has been authenticated.
         // ...
       } else {
         // Scenario: The PIN has not been authenticated.
         // ...
       }
     } catch (error) {
       // Scenario: The PIN authentication status fails to be obtained.
       result.resultCode = res.resultCode
       console.error(`promise: onGetUkeyPinAuthState failed`);
     }
     return Promise.resolve(result);
   }
   ```

   (6) **onClearUkeyPinAuthState** resets the PIN authentication state. When the call is successful, the value of the **resultCode** member in the return value is **0**. If the call fails, **resultCode** carries an error code

   ```ts
   onClearUkeyPinAuthState(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
     // ...
     let result: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
     };

     let res: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
     }
     try {
       // Scenario: The PIN authentication status is successfully cleared.
       let driver: YourUKeyDriver = YourDriverInstance;
       res = driver.YourDriver_onClearUkeyPinAuthState(...);
       result.resultCode = res.resultCode
     } catch (error) {
       // Scenario: The PIN authentication status fails to be cleared.
       result.resultCode = res.resultCode
       console.error(`promise: onClearUkeyPinAuthState failed`);
     }
     return Promise.resolve(result);
   }
   ```

   (7) **onInitSession** initializes the key session during Ukey signature verification. The application identity can be carried by the [HUKS_EXT_CRYPTO_TAG_UID](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag) parameter in **param**. When the call is successful, the value of the **resultCode** member is **0** and **handle** is left empty in the return value. If the call fails, **resultCode** carries an error code

   ```ts
   onInitSession(handle: string, params: huks.HuksOptions): Promise<HuksCryptoExtensionResult> {
     // ...
     let result: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
       handle: ""
     };

     let res: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
     }
     try {
       // Scenario: The initialization phase in the three-segment operations is successful.
       let driver: YourUKeyDriver = YourDriverInstance;
       res = driver.YourDriver_onInitSession(...);
       result.resultCode = res.resultCode
       result.handle = res.handle
     } catch (error) {
       // Scenario: The initialization phase in the three-segment operations fails.
       result.resultCode = res.resultCode
       console.error(`promise: onInitSession failed`);
     }
     return Promise.resolve(result);
   }
   ```

   (8) **onUpdateSession** transfers a large amount of data in segments during Ukey signature verification. The application identity can be carried by the [HUKS_EXT_CRYPTO_TAG_UID](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag) parameter in **param**. When the call is successful, the value of the **resultCode** member in the return value is **0**. If the call fails, **resultCode** carries an error code

   ```ts
   onUpdateSession(handle: string, params: huks.HuksOptions): Promise<HuksCryptoExtensionResult> {
     // ...
     let certs: Uint8Array = new Uint8Array();
     let result: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
       outData: certs
     };

     let res: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
     }
     try {
       // Scenario: The update phase in the three-segment operations is successful.
       let driver: YourUKeyDriver = YourDriverInstance;
       res = driver.YourDriver_onUpdateSession(...);
       result.resultCode = res.resultCode
       result.outData = res.outData
     } catch (error) {
       // Scenario: The update phase in the three-segment operations fails.
       result.resultCode = res.resultCode
       console.error(`promise: onUpdateSession failed`);
     }
     return Promise.resolve(result);
   }
   ```

   (9) **onFinishSession** transfers the last block of plaintext during Ukey signature operations and transfers the signature for verification. The application identity can be carried by the [HUKS_EXT_CRYPTO_TAG_UID](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag) parameter in **param**. When the call is successful, the value of the **resultCode** member in the return value is **0**. If the call fails, **resultCode** carries an error code

   ```ts
   onFinishSession(handle: string, params: huks.HuksOptions): Promise<HuksCryptoExtensionResult> {
     // ...
     let certs: Uint8Array = new Uint8Array();
     let result: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
       outData: certs
     };

     let res: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
     };
     try {
       // Scenario: The finish phase in the three-segment operations is successful.
       let driver: YourUKeyDriver = YourDriverInstance;
       res = driver.YourDriver_onFinishSession(...);
       result.resultCode = res.resultCode
       result.outData = res.outData
     } catch (error) {
       // Scenario: The finish phase in the three-segment operations fails.
       result.resultCode = res.resultCode
       console.error(`promise: onFinishSession failed`);
     }
     return Promise.resolve(result);
   }
   ```

   (10) **onExportCertificate** queries the certificate of a resource with the specified ID. You can parse the [HUKS_EXT_CRYPTO_TAG_PURPOSE](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag) parameter to obtain the certificate type required by the service. If this parameter is not specified, the signature certificate is obtained by default.<br>The values are as follows:<br>**0**: default usage.<br>**1**: used to query of all credentials.<br>**2**: used for credential signing.<br>**3**: used for credential encryption.

   ```ts
   onExportCertificate(resourceId: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
     // ...
     let certInfoSetArray: Array<HuksCryptoExtensionCertInfo> = []
     let result: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
       certs: certInfoSetArray
     };

     let res: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
     }
     try {
       // Scenario: The certificate is exported successfully.
       let driver: YourUKeyDriver = YourDriverInstance;
       res = driver.YourDriver_onExportCertificate(...);
       result.resultCode = res.resultCode
       result.certs = res.certs
     } catch (error) {
       // Scenario: The certificate fails to be exported.
       result.resultCode = res.resultCode
       console.error(`promise: onExportCertificate failed`);
     }
     return Promise.resolve(result);
   }
   ```

   (11) **onEnumCertificates** enumerates the certificate list during Ukey signature verification. The application identity can be carried by the [HUKS_EXT_CRYPTO_TAG_UID](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag) parameter in **params**. If the call is successful, **resultCode** is set to **0**, and the value of **certs** contains the certificate list (type: Array<[HuksCryptoExtensionCertInfo](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#hukscryptoextensioncertinfo)>) in the return value. If the call fails, **resultCode** carries an error code

   ```ts
   onEnumCertificates(params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
     // ...
     let certInfoSetArray: Array<HuksCryptoExtensionCertInfo> = []
     let result: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
       certs: certInfoSetArray
     };

     let res: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
     }
     try {
       // Scenario: All the certificates are exported successfully.
       let driver: YourUKeyDriver = YourDriverInstance;
       res = driver.YourDriver_onEnumCertificates(...);
       result.resultCode = res.resultCode
       result.certs = res.certs
     } catch (error) {
       // Scenario: All the certificates fail to be exported.
       result.resultCode = res.resultCode
       console.error(`promise: onEnumCertificates failed`);
     }
     return Promise.resolve(result);
   }
   ```

## Registration and Unregistration of CryptoExtensionAbility Adaptation for Driver Applications

### Registering CryptoExtensionAbility

When detecting that any Ukey device exists (for example, a Ukey device is inserted, the driver HAP registers **CryptoExtensionAbility** with the system. .

**Example**

```ts
// ./ets/cryptoability/CryptoAbility.ts

import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';

let ExtPropertiesTemp: Array<huksExternalCrypto.HuksExternalCryptoParam> = [
  {
      tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_ABILITY_NAME,
      value: stringToUint8Array("YourCryptoExtensionName")
  }
]

// Provider name. To ensure global uniqueness, it is recommended that the name contain the vendor information.
let provider = "testProvider"
huksExternalCrypto.registerProvider(provider, ExtPropertiesTemp);
```

### Unregistering CryptoExtensionAbility

When detecting that no Ukey device exists (for example, a Ukey device is removed), the driver HAP unregisters **CryptoExtensionAbility** from the system. .

**Example**

```ts
huksExternalCrypto.unregisterProvider(provider, ExtPropertiesTemp);
```
