# CryptoExtensionAbility Adaptation Development Guide

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

## Adaptation Guide

This guide provides the reference for driver vendors to inherit the API capabilities required for implementing [CryptoExtensionAbility](../../reference/apis-ability-kit/js-apis-app-ability-extensionAbility.md). Other implementations need to call the underlying driver functions encapsulated by the drivers in sequence based on service requirements.

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
   > 1. The function of exporting a public key must be implemented in **onGetProperty** so that the upstream services can use the PIN for encrypted transmission and complete PIN authentication. The encryption algorithms support RSA, SM2, and others. When the input parameter **propertyId** is set to **SKF_ExportPublicKey**, the returned public key information is in JSON format and contains the following four mandatory fields: **publicKey** (public key data), **algo** (algorithm type and key length), **transformation** (cryptographic operation parameter, such as the padding mode), and **size** (public key data length). For details about the implementation, see the **onGetProperty** API in the following sample code.
   > 2. PIN authentication status needs to be isolated based on the UID. The input parameter **params** of the **onAuthUkeyPin** API contains the UID information of the service (the service identity can be obtained through [HUKS_EXT_CRYPTO_TAG_UID](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag)).
   > 3. The errors of the API functions cannot be returned in a customized manner. If the errors are not returned in the mode defined by the API, an exception occurs.
   > 4. The input parameter **params** of **onExportCertificate** contains the [HUKS_TAG_PURPOSE](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukstag) parameter.<br>The values are as follows:<br>**0**: default usage.<br>**1**: used to query of all credentials.<br>**2**: used for credential signing.<br>**3**: used for credential encryption.

   ```ts
   import { huks, huksExternalCrypto, CryptoExtensionAbility, HuksCryptoExtensionCertInfo, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';
   import { util } from '@kit.ArkTS'
   import { cryptoFramework } from '@kit.CryptoArchitectureKit'

   class CryptoExtension extends CryptoExtensionAbility {
     // ...
     onOpenResource(resourceId: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
       // Construct a result object. By default, the operation fails, and the return value is -1.
       let result: HuksCryptoExtensionResult = {
         resultCode: -1,
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
         resultCode: -1,
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
   
     onCloseResource(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
       // ...
       let result: HuksCryptoExtensionResult = {
         resultCode: -1,
       };
   
       let res: HuksCryptoExtensionResult = {
         resultCode: -1,
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
   
     onGetProperty(handle: string, propertyId: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
       // ...
       let emptyArray: Array<huksExternalCrypto.HuksExternalCryptoParam> = [];
       let result: HuksCryptoExtensionResult = {
         resultCode: -1,
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
         resultCode: -1,
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
         resultCode: -1,
         authState: huksExternalCrypto.HuksExternalPinAuthState.HUKS_EXT_CRYPTO_PIN_NO_AUTH,
         retryCount: 0
       };
   
       let res: HuksCryptoExtensionResult = {
         resultCode: -1,
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
   
     onGetUkeyPinAuthState(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
       // ...
       let result: HuksCryptoExtensionResult = {
         resultCode: -1,
         authState: 0
       };

       let res: HuksCryptoExtensionResult = {
         resultCode: -1,
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
   
     onClearUkeyPinAuthState(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
       // ...
       let result: HuksCryptoExtensionResult = {
         resultCode: -1,
       };

       let res: HuksCryptoExtensionResult = {
         resultCode: -1,
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
   
     onInitSession(handle: string, params: huks.HuksOptions): Promise<HuksCryptoExtensionResult> {
       // ...
       let result: HuksCryptoExtensionResult = {
         resultCode: -1,
         handle: ""
       };

       let res: HuksCryptoExtensionResult = {
         resultCode: -1,
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
   
     onUpdateSession(handle: string, params: huks.HuksOptions): Promise<HuksCryptoExtensionResult> {
       // ...
       let certs: Uint8Array = new Uint8Array();
       let result: HuksCryptoExtensionResult = {
         resultCode: -1,
         outData: certs
       };

       let res: HuksCryptoExtensionResult = {
         resultCode: -1,
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
   
     onFinishSession(handle: string, params: huks.HuksOptions): Promise<HuksCryptoExtensionResult> {
       // ...
       let certs: Uint8Array = new Uint8Array();
       let result: HuksCryptoExtensionResult = {
         resultCode: -1,
         outData: certs
       };

       let res: HuksCryptoExtensionResult = {
         resultCode: -1,
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
   
     onExportCertificate(resourceId: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
       // ...
       let certInfoSetArray: Array<HuksCryptoExtensionCertInfo> = []
       let result: HuksCryptoExtensionResult = {
         resultCode: -1,
         certs: certInfoSetArray
       };

       let res: HuksCryptoExtensionResult = {
         resultCode: -1,
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
   
     onEnumCertificates(params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
       // ...
       let certInfoSetArray: Array<HuksCryptoExtensionCertInfo> = []
       let result: HuksCryptoExtensionResult = {
         resultCode: -1,
         certs: certInfoSetArray
       };

       let res: HuksCryptoExtensionResult = {
         resultCode: -1,
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
   }
   ```

6. Construct **HuksCryptoExtensionResult** and convert error codes. For details about the error codes, see [HUKS Error Codes](../../reference/apis-universal-keystore-kit/errorcode-huks.md). If no requirement is specified, return SKF error codes.

   ```ts
   let huksResult: HuksCryptoExtensionResult = {
     resultCode: -1,
   }
   ```

7. Encapsulate the underlying Ukey driver to implement API calling. The following uses the driver of the SKF library as an example:

   ```ts
   import { HuksCryptoExtensionResult, HuksCryptoExtensionCertInfo } from '@kit.UniversalKeystoreKit';

   class YourUKeyDriver {
     YourDriver_onOpenResource(index, ...) {
       // ...
       // Call the corresponding SKF function to open the resource (application, device, or container) based on the index.
       SKF_OpenApplication();
       SKF_ConnectDev();
       SKF_OpenContainer();
       // ...
     }
   
     YourDriver_onCloseResource(handle, ...) {
       // ...
       // Call the corresponding SKF function to close the resource (application, device, or container) based on the index.
       SKF_CloseApplication();
       SKF_DisconnectDev();
       SKF_CloseContainer();
       // ...
     }
   
     // Open the corresponding API.
     YourDriver_onGetProperty(...) {
       // ...
       SKF_GetDevInfo();
       SKF_EnumDev();
       SKF_EnumContainer();
       SKF_EnumApplication();
       // ...
     }
   
     YourDriver_onAuthUkeyPin(pin, ...) {
       // ...
       SKF_VerifyPIN();
       // ...
     }
   
     YourDriver_onGetUkeyPinAuthState(...) {
       // ...
     }
   
     YourDriver_onClearUkeyPinAuthState(...) {
       // ...
       SKF_ClearSecureState();
       // ...
     }
   
     YourDriver_onInitSession(...) {
       // ...
       SKF_DigestInit();
       // ...
     }
   
     YourDriver_onUpdateSession(...) {
       // ...
       SKF_DigestUpdate();
       // ...
     }
   
     YourDriver_onFinishSession(...) {
       // ...
       SKF_DigestFinish();
       // ...
     }
   
     YourDriver_onExportCertificate(...) {
       // ...
       SKF_ExportCertificate();
       // ...
     }
   
     YourDriver_onEnumCertificates(...): HuksCryptoExtensionResult {
       // ...
       let huksResult: HuksCryptoExtensionResult = {
         resultCode: -1,
         certs: new Array<HuksCryptoExtensionCertInfo>()
       }
       for (...) {
         if (huksResult.certs != undefined) {
           huksResult.certs.push(SKF_ExportCertificate());
         }
       }
       return huksResult;
     }
   }
   ```

## Registration and Unregistration of CryptoExtensionAbility Adaption for Driver Applications

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
