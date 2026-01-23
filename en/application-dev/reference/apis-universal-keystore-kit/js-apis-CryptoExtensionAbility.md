# @ohos.security.CryptoExtensionAbility (Key Extension Ability)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

Provides the external key extension abilities, including resource management, PIN authentication management, cryptographic operations, and common operations.

Constraints on implementing **ExtensionAbility**:
1. Device management: A single ExtensionAbility implementation supports a maximum of 10 Ukey connections.
2. Handle management: Application-based resource handle management is supported for the same Ukey resource (for example, the key in a container).
   - Multiple OpenHarmony applications can access the same Ukey key resource. For example, after OpenHarmony application 1 opens container A, OpenHarmony application 2 can also open container A.
   - Multiple OpenHarmony applications can perform operations on the same Ukey key resource. For example, after OpenHarmony application 1 performs private key signing on container A, OpenHarmony application 2 can also perform private key signing on container A after verifying the PIN. The two applications do not affect each other.
3. Key session management: Init-Update-Finish key management is supported. A signature verification needs to be completed by using three functions ([onInitSession](#cryptoextensionabilityoninitsession), [onUpdateSession](#cryptoextensionabilityonupdatesession), [onFinishSession](#cryptoextensionabilityonfinishsession)). Session management and key session status caching are required.
   - **init**: Initializes the key session and returns the session handle information.
   - **update**: Passes group data, performs cryptographic operations on the group data, updates the key session information, and returns the intermediate data (if any).
   - **finish**: Passes the last group of data, returns the key, ends the key session, and returns the final result.
4. Authentication state management: Application-based authentication state management is supported. For application A in the same UKey, after OpenHarmony application 1 verifies the PIN of application A, OpenHarmony application 2 needs to verify the PIN again if it wants to access application A.
5. Certificate query: Enumeration of all certificates and query of certificates in a single container based on certificate type are supported.

> **Description**
>
> The initial APIs of this module are supported since API version 22. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { huks, huksExternalCrypto, CryptoExtensionAbility } from '@kit.UniversalKeystoreKit';
```

## HuksCryptoExtensionResultCode

Enumerates the values of **resultCode** in [HuksCryptoExtensionResult](#hukscryptoextensionresult).

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Security.Huks.CryptoExtension

| Name| Value| Description|
| ------ | ---- | ------ |
| HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL | 34800000 | Key extension error. Possible causes:<br>1. Invalid input parameters.<br>2. An unrecoverable error state occurs in the key extension.|
| HUKS_CRYPTO_EXTENSION_ERR_UKEY_NOT_EXIST | 34800001 | The UKey does not exist. Possible causes:<br>1. The UKey has been removed.<br>2. The key extension is in an incorrect UKey state.|
| HUKS_CRYPTO_EXTENSION_ERR_UKEY_DRIVER_FAIL | 34800002 | An unknown error occurs in the UKey driver.|
| HUKS_CRYPTO_EXTENSION_ERR_PIN_NO_AUTH | 34800003 | The UKey PIN is not authenticated. Authenticate the UKey PIN first.|
| HUKS_CRYPTO_EXTENSION_ERR_HANDLE_NOT_EXIST | 34800004 | The handle does not exist. Possible causes:<br>1. Invalid handle.<br>2. The HUKS service and key extension states are inconsistent. The handle held by the HUKS service fails to be released due to an exception.|
| HUKS_CRYPTO_EXTENSION_ERR_HANDLE_UNAVAILABLE | 34800005 | The handle is unavailable. Possible causes:<br>The key extension and Ukey states are inconsistent.|
| HUKS_CRYPTO_EXTENSION_ERR_PIN_INCORRECT | 34800006 | Incorrect UKey PIN. Check the entered PIN.|
| HUKS_CRYPTO_EXTENSION_ERR_PIN_LOCKED | 34800007 | The UKey PIN is locked. Possible causes:<br>Too many incorrect PIN entries.|

## HuksCryptoExtensionCertInfo

Defines the elements in the **certs** array of [HuksCryptoExtensionResult](#hukscryptoextensionresult).

**System capability**: SystemCapability.Security.Huks.CryptoExtension

| Name| Type   | Read-Only| Optional| Description |
| ------ | --------- | ---- | ---- | ------ |
| purpose    | [certificateManager.CertificatePurpose](../apis-device-certificate-kit/js-apis-certManager.md#certificatepurpose22)  | No  | No  | Purpose of the key corresponding to the certificate chain.|
| resourceId  | string | No  | No  | Resource ID.|
| cert  | Uint8Array | No  | No  | Certificate.|

## HuksCryptoExtensionResult

Defines the common return value types of APIs.

**System capability**: SystemCapability.Security.Huks.CryptoExtension

| Name| Type | Read-Only| Optional| Description|
| ------ | ------ | ---- | ---- | ------ |
| resultCode  | int | No  | No  | Error code.|
| handle  | string | No  | Yes  | Resource handle.|
| authState  | int | No  | Yes  | Authentication state.|
| retryCount  | int | No  | Yes  | Number of retry times.|
| certs  | Array<[HuksCryptoExtensionCertInfo](#hukscryptoextensioncertinfo)> | No  | Yes  | Certificate.|
| property  | Array<[huksExternalCrypto.HuksExternalCryptoParam](js-apis-huksExternalCrypto.md#huksexternalcryptoparam)> | No  | Yes  | Property.|
| outData  | int | No  | Yes  | Returned data.|

## CryptoExtensionAbility.onOpenResource

onOpenResource(resourceId: string, params: Array\<huksExternalCrypto.HuksExternalCryptoParam>): Promise\<HuksCryptoExtensionResult>

Opens a Ukey key resource based on the **resourceId** parameter. This API uses a promise to return the result.

**System capability**: SystemCapability.Security.Huks.CryptoExtension

**Parameters**

| Name  | Type| Mandatory| Description|
| -------- | --------- | ---- | -------- |
| resourceId | string | Yes  | Resource ID.|
| params  | Array\<[huksExternalCrypto.HuksExternalCryptoParam](js-apis-huksExternalCrypto.md#huksexternalcryptoparam)> | Yes  | Input parameters. The application is identified by the [HUKS_EXT_CRYPTO_TAG_UID](js-apis-huksExternalCrypto.md#huksexternalcryptotag) parameter.|

**Return value**

| Type| Description|
| ---------- | ----------- |
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise used to return the result. If the call is successful, **resultCode** is **0** and handle contains the resource handle information. If the call fails, **resultCode** contains the error code.<br>Possible error code values:<br>**34800000**: Key extension error.<br>**34800001**: Ukey does not exist.<br>**34800002**: Ukey driver error.<br>**34800004**: Handle does not exist.<br>For details, see [HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode).|

**Example**

```ts
import { huksExternalCrypto, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onOpenResource(resourceId: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
    // Parse resourceId, open the underlying handle, and map it to a new handle for return.
    let result: HuksCryptoExtensionResult = {
      resultCode: 0,
      handle: "test handle"
    };

    // ...
    return Promise.resolve(result)
  }
}
```

## CryptoExtensionAbility.onCloseResource

onCloseResource(handle: string, params: Array\<huksExternalCrypto.HuksExternalCryptoParam>): Promise\<HuksCryptoExtensionResult>

Closes the key resource of a Ukey based on the **handle** parameter. This API uses a promise to return the result.

**System capability**: SystemCapability.Security.Huks.CryptoExtension

**Parameters**

| Name  | Type| Mandatory| Description |
| -------- | ------ | ---- | ------ |
| handle | string | Yes  | Session handle. |
| params  | Array\<[huksExternalCrypto.HuksExternalCryptoParam](js-apis-huksExternalCrypto.md#huksexternalcryptoparam)> | Yes| Input parameters. The application is identified by the [HUKS_EXT_CRYPTO_TAG_UID](js-apis-huksExternalCrypto.md#huksexternalcryptotag) parameter.|

**Return value**

| Type| Description|
| ----------- | ------------- |
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise used to return the result. If the call is successful, **resultCode** is **0**, indicating that the resource is closed successfully. If the call fails, **resultCode** contains the error code.<br>Possible error code values:<br>**34800000**: Key extension error.<br>**34800002**: Ukey driver error.<br>**34800004**: Handle does not exist.<br>**34800005**: Handle is unavailable.<br>For details, see [HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode).|

**Example**

```ts
import { huksExternalCrypto, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onCloseResource(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
    // Close the handle. If the underlying handle needs to be closed, close it.
    const result: HuksCryptoExtensionResult = {
        resultCode: 0,
    };

    // ...
    return Promise.resolve(result)
  }
}
```

## CryptoExtensionAbility.onGetProperty

onGetProperty(handle: string, propertyId: string, params: Array\<huksExternalCrypto.HuksExternalCryptoParam>): Promise\<HuksCryptoExtensionResult>

Obtains the property based on the **handle** and **propertyId** parameters. This API uses a promise to return the result.

**System capability**: SystemCapability.Security.Huks.CryptoExtension

**Parameters**

| Name  | Type | Mandatory| Description |
| -------- | ----- | ---- | ------|
| handle | string | Yes  | Resource handle.|
| propertyId | string | Yes  | Property name for the search operation, which is the SKF API name defined in GMT 0016-2023. The service needs to be adapted to the API name.|
| params  | Array\<[huksExternalCrypto.HuksExternalCryptoParam](js-apis-huksExternalCrypto.md#huksexternalcryptoparam)> | Yes| Input parameters. The application is identified by the [HUKS_EXT_CRYPTO_TAG_UID](js-apis-huksExternalCrypto.md#huksexternalcryptotag) parameter.|

**Return value**

| Type   | Description  |
| -------- | -----------|
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise used to return the result. If the call is successful, **resultCode** is **0**, and the **property** of **HuksCryptoExtensionResult** contains the obtained property carried by the [HUKS_EXT_CRYPTO_TAG_EXTRA_DATA](js-apis-huksExternalCrypto.md#huksexternalcryptotag) parameter. If the call fails, **resultCode** contains the error code.<br>Possible error code values:<br>**34800000**: Key extension error.<br>**34800002**: Ukey driver error.<br>**34800003**: Ukey PIN is not authenticated.<br>**34800004**: Handle does not exist.<br>**34800005**: Handle is unavailable.<br>**34800007**: Ukey PIN is locked.<br>For details, see [HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode).|

**Example**

```ts
import { huksExternalCrypto, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onGetProperty(handle: string, propertyId: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
    // Execute the related function based on propertyId. The function parameters are obtained from params. The output data is encapsulated in the property field of the return value and carried by HUKS_EXT_CRYPTO_TAG_EXTRA_DATA.
    const emptyArray: Array<huksExternalCrypto.HuksExternalCryptoParam> = [];
    const result: HuksCryptoExtensionResult = {
      resultCode: 0,
      property: emptyArray
    };

    // ...
    return Promise.resolve(result)
  }
}
```

## CryptoExtensionAbility.onAuthUkeyPin

onAuthUkeyPin(handle: string, params: Array\<huksExternalCrypto.HuksExternalCryptoParam>): Promise\<HuksCryptoExtensionResult>

Requests the Ukey PIN authentication. This API uses a promise to return the result.

**System capability**: SystemCapability.Security.Huks.CryptoExtension

**Parameters**

| Name  | Type  | Mandatory| Description  |
| ------ | ------ | ---- | ------- |
| handle | string  | Yes  | Resource handle.  |
| params  | Array\<[huksExternalCrypto.HuksExternalCryptoParam](js-apis-huksExternalCrypto.md#huksexternalcryptoparam)> | Yes  | Input parameters. The application is identified by the [HUKS_EXT_CRYPTO_TAG_UID](js-apis-huksExternalCrypto.md#huksexternalcryptotag) parameter.|

**Return value**

| Type| Description|
| -------- | --------|
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise used to return the result. If the call is successful, **resultCode** is **0** and **authState** is not **0**, indicating that the authentication request is successful. If the call fails, **resultCode** contains the error code.<br>Possible error code values:<br>**34800000**: Key extension error.<br>**34800002**: Ukey driver error.<br>**34800004**: Handle does not exist.<br>**34800005**: Handle is unavailable.<br>**34800006**: Ukey PIN error.<br>**34800007**: Ukey PIN is locked.<br>For details, see [HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode).|

**Example**

```ts
import { huksExternalCrypto, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onAuthUkeyPin(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
    // Perform PIN authentication and maintain the PIN authentication state of the application.
    const result: HuksCryptoExtensionResult = {
      resultCode: 0,
      authState: 1
    };

    // ...
    return Promise.resolve(result)
  }
}
```

## CryptoExtensionAbility.onGetUkeyPinAuthState

onGetUkeyPinAuthState(handle: string, params: Array\<huksExternalCrypto.HuksExternalCryptoParam>): Promise\<HuksCryptoExtensionResult>

Obtains the PIN authentication state of a Ukey. This API uses a promise to return the result.

**System capability**: SystemCapability.Security.Huks.CryptoExtension

**Parameters**

| Name  | Type | Mandatory| Description  |
| -------- | ------- | ---- | -------|
| handle | string | Yes  | Resource handle.|
| params  | Array\<[huksExternalCrypto.HuksExternalCryptoParam](js-apis-huksExternalCrypto.md#huksexternalcryptoparam)> | Yes  | Input parameters. The application is identified by the [HUKS_EXT_CRYPTO_TAG_UID](js-apis-huksExternalCrypto.md#huksexternalcryptotag) parameter.|

**Return value**

| Type  | Description |
| -------- | ------- |
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise used to return the result. If the call is successful, **resultCode** is **0**, and the **authState** of **HuksCryptoExtensionResult** contains the obtained PIN authentication state. If the call fails, **resultCode** contains the error code.<br>Possible error code values:<br>**34800000**: Key extension error.<br>**34800002**: Ukey driver error.<br>**34800004**: Handle does not exist.<br>**34800005**: Handle is unavailable.<br>For details, see [HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode).|

**Example**

```ts
import { huksExternalCrypto, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onGetUkeyPinAuthState(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
    // Query the PIN authentication state.
    const result: HuksCryptoExtensionResult = {
      resultCode: 0,
      authState: 1
    };

    // ...
    return Promise.resolve(result)
  }
}
```

## CryptoExtensionAbility.onClearUkeyPinAuthState

onClearUkeyPinAuthState(handle: string, params: Array\<huksExternalCrypto.HuksExternalCryptoParam>): Promise\<HuksCryptoExtensionResult>

Clears the PIN authentication state of the application. This API uses a promise to return the result.

**System capability**: SystemCapability.Security.Huks.CryptoExtension

**Parameters**

| Name  | Type  | Mandatory| Description|
| -------- | ----- | ---- | ------|
| handle  | string | Yes  | Session handle.|
| params  | Array\<[huksExternalCrypto.HuksExternalCryptoParam](js-apis-huksExternalCrypto.md#huksexternalcryptoparam)> | Yes  | Input parameters. The application is identified by the [HUKS_EXT_CRYPTO_TAG_UID](js-apis-huksExternalCrypto.md#huksexternalcryptotag) parameter.|

**Return value**

| Type| Description|
| ------------ | ---------|
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise used to return the result. If the call is successful, **resultCode** is **0**, indicating that the PIN authentication state is cleared successfully. If the call fails, **resultCode** contains the error code.<br>Possible error code values:<br>**34800000**: Key extension error.<br>**34800002**: Ukey driver error.<br>**34800004**: Handle does not exist.<br>**34800005**: Handle is unavailable.<br>For details, see [HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode).|

**Example**

```ts
import { huksExternalCrypto, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onClearUkeyPinAuthState(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
    const result: HuksCryptoExtensionResult = {
      resultCode: 0
    };

    // ...
    return Promise.resolve(result)
  }
}
```

## CryptoExtensionAbility.onInitSession

onInitSession(handle: string, params: huks.HuksOptions): Promise\<HuksCryptoExtensionResult>

Initializes a key session. (The first operation of the Init-Update-Finish process.) This API uses a promise to return the result.

**System capability**: SystemCapability.Security.Huks.CryptoExtension

**Parameters**

| Name  | Type| Mandatory| Description|
| -------- | ----- | ---- | ------- |
| handle | string                      | Yes  | Resource handle.|
| params  | [HuksOptions](js-apis-huks.md#huksoptions)  | Yes  | Input parameters. The application is identified by the [HUKS_EXT_CRYPTO_TAG_UID](js-apis-huksExternalCrypto.md#huksexternalcryptotag) parameter.|

**Return value**

| Type| Description|
| --------- | ---------|
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise used to return the result. If the call is successful, **resultCode** is **0** and **handle** is not empty. If the call fails, **resultCode** contains the error code.<br>Possible error code values:<br>**34800000**: Key extension error.<br>**34800002**: Ukey driver error.<br>**34800003**: Ukey PIN is not authenticated.<br>**34800004**: Handle does not exist.<br>**34800005**: Handle is unavailable.<br>**34800007**: Ukey PIN is locked.<br>For details, see [HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode).|

**Example**

```ts
import { huks, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onInitSession(handle: string, params: huks.HuksOptions): Promise<HuksCryptoExtensionResult> {
    const result: HuksCryptoExtensionResult = {
      resultCode: 0,
      handle: "test handle"
    };

    // ...
    return Promise.resolve(result)
  }
}
```

## CryptoExtensionAbility.onUpdateSession

onUpdateSession(handle: string, params: huks.HuksOptions): Promise\<HuksCryptoExtensionResult>

Updates a key session. (The second operation of the Init-Update-Finish process.) This API uses a promise to return the result.

**System capability**: SystemCapability.Security.Huks.CryptoExtension

**Parameters**

| Name  | Type | Mandatory| Description|
| -------- | ----- | ---- | ------|
| handle | string | Yes  | Resource handle.  |
| params  | [HuksOptions](js-apis-huks.md#huksoptions)  | Yes  | Input parameters. The application is identified by the [HUKS_EXT_CRYPTO_TAG_UID](js-apis-huksExternalCrypto.md#huksexternalcryptotag) parameter.|

**Return value**

| Type| Description|
| --------- | ---------|
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise used to return the result. If the call is successful, **resultCode** is **0**. If the call fails, **resultCode** contains the error code.<br>Possible error code values:<br>**34800000**: Key extension error.<br>**34800002**: Ukey driver error.<br>**34800003**: Ukey PIN is not authenticated.<br>**34800004**: Handle does not exist.<br>**34800005**: Handle is unavailable.<br>**34800007**: Ukey PIN is locked.<br>For details, see [HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode).|

**Example**

```ts
import { huks, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onUpdateSession(initHandle: string, params: huks.HuksOptions): Promise<HuksCryptoExtensionResult> {
    let outBuffer: Uint8Array = new Uint8Array(1024);
    const result: HuksCryptoExtensionResult = {
      resultCode: 0,
      outData: outBuffer
    };

    // ...
    return Promise.resolve(result)
  }
}
```

## CryptoExtensionAbility.onFinishSession

onFinishSession(handle: string, params: huks.HuksOptions): Promise\<HuksCryptoExtensionResult>

Ends a key session. (The last operation of the Init-Update-Finish process.) This API uses a promise to return the result.

**System capability**: SystemCapability.Security.Huks.CryptoExtension

**Parameters**

| Name  | Type| Mandatory| Description |
| -------- | -------- | ---- | --------- |
| handle | string  | Yes  | Resource handle.|
| params  | [HuksOptions](js-apis-huks.md#huksoptions)  | Yes  | Input parameters. The application is identified by the [HUKS_EXT_CRYPTO_TAG_UID](js-apis-huksExternalCrypto.md#huksexternalcryptotag) parameter, and the algorithm parameters (such as the algorithm type and padding mode) are also included.|

**Return value**

| Type| Description|
| ------- | ---------- |
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise used to return the result. If the call is successful, **resultCode** is **0**. If the call fails, **resultCode** contains the error code.<br>Possible error code values:<br>**34800000**: Key extension error.<br>**34800002**: Ukey driver error.<br>**34800003**: Ukey PIN is not authenticated.<br>**34800004**: Handle does not exist.<br>**34800005**: Handle is unavailable.<br>**34800007**: Ukey PIN is locked.<br>For details, see [HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode).|

**Example**

```ts
import { huks, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onFinishSession(initHandle: string, params: huks.HuksOptions): Promise<HuksCryptoExtensionResult> {
    let outBuffer: Uint8Array = new Uint8Array(1024);
    const result: HuksCryptoExtensionResult = {
      resultCode: 0,
      outData: outBuffer
    };

    // ...
    return Promise.resolve(result)
  }
}
```

## CryptoExtensionAbility.onExportCertificate

onExportCertificate(resourceId: string, params?: Array\<huksExternalCrypto.HuksExternalCryptoParam>): Promise\<HuksCryptoExtensionResult>

Queries the certificate of a specified resource ID. This API uses a promise to return the result.

**System capability**: SystemCapability.Security.Huks.CryptoExtension

**Parameters**

| Name  | Type | Mandatory| Description|
| -------- | ---------- | ---- | --------- |
| resourceId | string | Yes  | Resource ID. It is attached to [HuksCryptoExtensionCertInfo](#hukscryptoextensioncertinfo).|
| params  | Array\<[huksExternalCrypto.HuksExternalCryptoParam](js-apis-huksExternalCrypto.md#huksexternalcryptoparam)>  | No  | Operation parameters. By default, the certificate of the signature type is obtained. You can also use the [HUKS_EXT_CRYPTO_TAG_PURPOSE](js-apis-huksExternalCrypto.md#huksexternalcryptotag) parameter to specify the certificate type, including signing and signature verification as well as encryption and decryption.|

**Return value**

| Type | Description |
| ---------- | --------- |
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise used to return the result. If the call is successful, **certs** contains the single certificate obtained. If the call fails, **resultCode** contains the error code.<br>Possible error code values:<br>**34800000**: Key extension error.<br>**34800001**: Ukey does not exist.<br>**34800002**: Ukey driver error.<br>**34800004**: Handle does not exist.<br>For details, see [HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode).|

**Example**

```ts
import { huksExternalCrypto, CryptoExtensionAbility, HuksCryptoExtensionResult,
  HuksCryptoExtensionCertInfo } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onExportCertificate(resourceId: string, params?: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
    const certInfoSetArray: Array<HuksCryptoExtensionCertInfo> = []
    const result: HuksCryptoExtensionResult = {
      resultCode: 0,
      certs: certInfoSetArray
    };

    // ...
    return Promise.resolve(result)
  }
}
```

## CryptoExtensionAbility.onEnumCertificates

onEnumCertificates(params?: Array\<huksExternalCrypto.HuksExternalCryptoParam>): Promise\<HuksCryptoExtensionResult>

Obtains the certificate information of all UKey devices under an extension. This API uses a promise to return the result.

**System capability**: SystemCapability.Security.Huks.CryptoExtension

**Parameters**

| Name  | Type| Mandatory| Description  |
| -------- | -----| ---- | ---------- |
| params  | Array\<[huksExternalCrypto.HuksExternalCryptoParam](js-apis-huksExternalCrypto.md#huksexternalcryptoparam)>  | No  | Operation parameters. By default, the [certificate](../../security/DeviceCertificateKit/certManager-overview.md) of the signature type is obtained. You can also use the [HUKS_EXT_CRYPTO_TAG_PURPOSE](js-apis-huksExternalCrypto.md#huksexternalcryptotag) parameter to specify the type of the certificate to be obtained. The supported types include signing and signature verification, as well as encryption and decryption.|

**Return value**

| Type| Description|
| ---------- | ---------|
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise used to return the result. If the call is successful, **certs** contains all the obtained certificates. If the call fails, **resultCode** contains the error code.<br>Possible error code values:<br>**34800000**: Key extension error.<br>**34800001**: Ukey does not exist.<br>**34800002**: Ukey driver error.<br>For details, see [HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode).|

**Example**

```ts
import { huksExternalCrypto, CryptoExtensionAbility, HuksCryptoExtensionResult,
  HuksCryptoExtensionCertInfo } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onEnumCertificates(params?: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
    const certInfoSetArray: Array<HuksCryptoExtensionCertInfo> = []
    const result: HuksCryptoExtensionResult = {
      resultCode: 0,
      certs: certInfoSetArray
    };

    // ...
    return Promise.resolve(result)
  }
}
```
