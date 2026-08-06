# @ohos.security.CryptoExtensionAbility (Key Extension Ability)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

Provides the external key extension abilities, including resource management, PIN authentication management, cryptographic operations, and common operations.

Functions and restrictions of **ExtensionAbility**:
1. Device management: A single **ExtensionAbility** implementation supports a maximum of 10 UKey connections.
2. Handle management: Application-based handle resource management is supported for the same UKey resource (for example, the keys in a container).
   - Multiple OpenHarmony applications can open the same UKey key resource. For example, after OpenHarmony application 1 opens container A, OpenHarmony application 2 can also open container A.
   - Multiple OpenHarmony applications can operate the same UKey key resource. For example, after OpenHarmony application 1 performs private key signing on container A, OpenHarmony application 2 can also perform private key signing on container A after verifying the PIN. The two applications do not affect each other.
3. Key session management: Three-segment key management is supported. Signature verification for a single signature requires the [onInitSession](#oninitsession)/[onUpdateSession](#onupdatesession)/[onFinishSession](#onfinishsession) functions to be used together in three steps. In addition, session management and key session status caching are supported.
   - **init**: Initializes the key session and returns the session handle information.
   - **update**: Passes group data, performs cryptographic operations on the group data, updates the key session information, and returns the intermediate data (if any).
   - **finish**: Passes the last group of data, returns the key, ends the key session, and returns the final result.
4. Authentication state management: Application-based authentication state management is supported. After OpenHarmony application 1 verifies the PIN of UKey application A, if OpenHarmony application 2 needs to access UKey application A, PIN authentication is also required.
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
| HUKS_CRYPTO_EXTENSION_ERR_PIN_NO_AUTH | 34800003 | The UKey PIN is not authenticated. Authenticate the UKey PIN first by calling [onAuthUkeyPin](#onauthukeypin).|
| HUKS_CRYPTO_EXTENSION_ERR_HANDLE_NOT_EXIST | 34800004 | The handle does not exist. Possible causes:<br>1. Invalid handle.<br>2. The HUKS service and key extension states are inconsistent. The handle held by the HUKS service fails to be released due to an exception.|
| HUKS_CRYPTO_EXTENSION_ERR_HANDLE_UNAVAILABLE | 34800005 | The handle is unavailable. Possible causes:<br>The key extension and UKey states are inconsistent.|
| HUKS_CRYPTO_EXTENSION_ERR_PIN_INCORRECT | 34800006 | Incorrect UKey PIN. Check the entered PIN.|
| HUKS_CRYPTO_EXTENSION_ERR_PIN_LOCKED | 34800007 | The UKey PIN is locked. Possible causes:<br>Too many incorrect PIN entries.|

## HuksCryptoExtensionCertInfo

Defines the elements in the **certs** array of [HuksCryptoExtensionResult](#hukscryptoextensionresult).

**System capability**: SystemCapability.Security.Huks.CryptoExtension

| Name| Type   | Read-Only| Optional| Description |
| ------ | --------- | ---- | ---- | ------ |
| purpose    | [certificateManager.CertificatePurpose](../apis-device-certificate-kit/js-apis-certManager.md#certificatepurpose22)  | No  | No  | Purpose of the key corresponding to the certificate chain.|
| resourceId  | string | No  | No  | Resource ID, in JSON format, which can be mapped to a resource in the UKey.|
| cert  | Uint8Array | No  | No  | Certificate.|

## HuksCryptoExtensionResult

Defines the common return value types of APIs.

**System capability**: SystemCapability.Security.Huks.CryptoExtension

| Name| Type | Read-Only| Optional| Description|
| ------ | ------ | ---- | ---- | ------ |
| resultCode  | number | No  | No  | Error code.|
| handle  | string | No  | Yes  | Resource handle.|
| authState  | number | No  | Yes  | Authentication state.|
| retryCount  | number | No  | Yes  | Number of remaining PIN authentication attempts. If the value is **0**, there are no remaining attempts.|
| certs  | Array<[HuksCryptoExtensionCertInfo](#hukscryptoextensioncertinfo)> | No  | Yes  | Certificate.|
| property  | Array<[huksExternalCrypto.HuksExternalCryptoParam](js-apis-huksExternalCrypto.md#huksexternalcryptoparam)> | No  | Yes  | Property.|
| outData  | Uint8Array | No  | Yes  | Returned data.|
| resourceId | string | No| Yes| Returned resource ID. The default value is empty.<br>**Since**: 26.0.0<br>**Model restriction**: This API can be used only in the stage model.|

## CryptoExtensionAbility

Provides the key extension capabilities, including API description required for external key management extension, such as enabling/disabling resources, PIN authentication management, key session operations, certificate management, key generation and import, and common operations. The driver vendor needs to inherit **CryptoExtensionAbility** and implement related APIs. After the capabilities are registered using [registerProvider](js-apis-huksExternalCrypto.md#huksexternalcryptoregisterprovider), HUKS and certificate management open the corresponding key management extension capabilities to applications.

**CryptoExtensionAbility** can isolate the implementation differences of Ukey driver vendors.

**System capability**: SystemCapability.Security.Huks.CryptoExtension

### onOpenResource

onOpenResource(resourceId: string, params: Array\<huksExternalCrypto.HuksExternalCryptoParam>): Promise\<HuksCryptoExtensionResult>

Opens the UKey key resource based on the **resourceId** parameter. This API uses a promise to return the result.

**System capability**: SystemCapability.Security.Huks.CryptoExtension

**Parameters**

| Name  | Type| Mandatory| Description|
| -------- | --------- | ---- | -------- |
| resourceId | string | Yes  | Resource ID.|
| params  | Array\<[huksExternalCrypto.HuksExternalCryptoParam](js-apis-huksExternalCrypto.md#huksexternalcryptoparam)> | Yes  | Input parameters. The application is identified by the [HUKS_EXT_CRYPTO_TAG_UID](js-apis-huksExternalCrypto.md#huksexternalcryptotag) parameter.|

**Return value**

| Type| Description|
| ---------- | ----------- |
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise used to return the result. If the call is successful, **resultCode** is **0** and handle contains the resource handle information. If the call fails, **resultCode** contains the error code.<br>Possible error code values:<br>**34800000**: Key extension error.<br>**34800001**: The UKey does not exist.<br>**34800002**: UKey driver error.<br>**34800004**: The handle does not exist.<br>For details, see [HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode).|

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
    return Promise.resolve(result);
  }
}
```

### onCloseResource

onCloseResource(handle: string, params: Array\<huksExternalCrypto.HuksExternalCryptoParam>): Promise\<HuksCryptoExtensionResult>

Closes the key resource of a UKey based on the **handle** parameter. This API uses a promise to return the result.

**System capability**: SystemCapability.Security.Huks.CryptoExtension

**Parameters**

| Name  | Type| Mandatory| Description |
| -------- | ------ | ---- | ------ |
| handle | string | Yes  | Session handle. |
| params  | Array\<[huksExternalCrypto.HuksExternalCryptoParam](js-apis-huksExternalCrypto.md#huksexternalcryptoparam)> | Yes| Input parameters. The application is identified by the [HUKS_EXT_CRYPTO_TAG_UID](js-apis-huksExternalCrypto.md#huksexternalcryptotag) parameter.|

**Return value**

| Type| Description|
| ----------- | ------------- |
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise used to return the result. If the call is successful, **resultCode** is **0**, indicating that the resource is closed successfully. If the call fails, **resultCode** contains the error code.<br>Possible error code values:<br>34800000 Key extension error.<br>34800002 UKey driver error.<br>34800004 Handle does not exist.<br>34800005 The handle is unavailable.<br>For details, see [HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode).|

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
    return Promise.resolve(result);
  }
}
```

### onGetProperty

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
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise used to return the result. If the call is successful, **resultCode** is **0**, and the **property** of **HuksCryptoExtensionResult** contains the obtained property carried by the [HUKS_EXT_CRYPTO_TAG_EXTRA_DATA](js-apis-huksExternalCrypto.md#huksexternalcryptotag) parameter. If the call fails, **resultCode** contains the error code.<br>Possible error code values:<br>34800000 Key extension error.<br>34800002 UKey driver error.<br>34800003 The UKey PIN is not authenticated.<br>34800004 Handle does not exist.<br>34800005 The handle is unavailable.<br>34800007 The UKey PIN is locked.<br>For details, see [HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode).|

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
    return Promise.resolve(result);
  }
}
```

### onSetProperty

onSetProperty(handle: string, propertyId: string, params: Array\<huksExternalCrypto.HuksExternalCryptoParam>): Promise\<HuksCryptoExtensionResult>

Sets the property based on the **handle** and **propertyId** parameters. This API uses a promise to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Security.Huks.CryptoExtension

**Parameters**

| Name  | Type | Mandatory| Description |
| -------- | ----- | ---- | ------|
| handle | string | Yes  | Resource handle.|
| propertyId | string | Yes  | Property name for the setting operation. You are advised to use the name of the corresponding SKF API defined in GMT 0016-2023 as the property ID.|
| params  | Array\<[huksExternalCrypto.HuksExternalCryptoParam](js-apis-huksExternalCrypto.md#huksexternalcryptoparam)> | Yes| Input parameter, which contains the operation parameters related to **propertyId**. The application is identified by the [HUKS_EXT_CRYPTO_TAG_UID](js-apis-huksExternalCrypto.md#huksexternalcryptotag) parameter.|

**Return value**

| Type   | Description  |
| -------- | -----------|
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise used to return the result. If the call is successful, the value of **resultCode** is **0**, indicating that the property is set successfully. If the call fails, **resultCode** contains the error code.<br>Possible error code values:<br>34800000 Key extension error. Possible causes:<br>1. Invalid input parameters.<br>2. An unrecoverable error state occurs in the key extension.<br>34800002 UKey driver error.<br>34800003 The UKey PIN is not authenticated. Authenticate the UKey PIN first.<br>34800004 Handle does not exist. Possible causes:<br>1. Invalid handle.<br>2. The HUKS service and key extension states are inconsistent. The handle held by the HUKS service fails to be released due to an exception.<br>34800005 The handle is unavailable. Possible causes:<br>The key extension and UKey states are inconsistent.<br>34800007 The UKey PIN is locked. Possible causes:<br>Too many incorrect PIN entries.<br>For details, see [HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode).|

**Example**

```ts
import { huksExternalCrypto, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onSetProperty(handle: string, propertyId: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
    // Perform related setting operations based on propertyId. The operation parameters are obtained from params.
    const result: HuksCryptoExtensionResult = {
      resultCode: 0
    };

    // ...
    return Promise.resolve(result);
  }
}
```

### onAuthUkeyPin

onAuthUkeyPin(handle: string, params: Array\<huksExternalCrypto.HuksExternalCryptoParam>): Promise\<HuksCryptoExtensionResult>

Requests the UKey PIN authentication. This API uses a promise to return the result.

**System capability**: SystemCapability.Security.Huks.CryptoExtension

**Parameters**

| Name  | Type  | Mandatory| Description  |
| ------ | ------ | ---- | ------- |
| handle | string  | Yes  | Resource handle.  |
| params  | Array\<[huksExternalCrypto.HuksExternalCryptoParam](js-apis-huksExternalCrypto.md#huksexternalcryptoparam)> | Yes  | Input parameters. The application is identified by the [HUKS_EXT_CRYPTO_TAG_UID](js-apis-huksExternalCrypto.md#huksexternalcryptotag) parameter.|

**Return value**

| Type| Description|
| -------- | --------|
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise used to return the result. If the call is successful, **resultCode** is **0** and **authState** is not **0**, indicating that the authentication request is successful. If the call fails, **resultCode** contains the error code.<br>Possible error code values:<br>34800000 Key extension error.<br>34800002 UKey driver error.<br>34800004 Handle does not exist.<br>34800005 The handle is unavailable.<br>34800006 Incorrect UKey PIN.<br>34800007 The UKey PIN is locked.<br>For details, see [HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode).|

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
    return Promise.resolve(result);
  }
}
```

### onGetUkeyPinAuthState

onGetUkeyPinAuthState(handle: string, params: Array\<huksExternalCrypto.HuksExternalCryptoParam>): Promise\<HuksCryptoExtensionResult>

Obtains the PIN authentication state of a UKey. This API uses a promise to return the result.

**System capability**: SystemCapability.Security.Huks.CryptoExtension

**Parameters**

| Name  | Type | Mandatory| Description  |
| -------- | ------- | ---- | -------|
| handle | string | Yes  | Resource handle.|
| params  | Array\<[huksExternalCrypto.HuksExternalCryptoParam](js-apis-huksExternalCrypto.md#huksexternalcryptoparam)> | Yes  | Input parameters. The application is identified by the [HUKS_EXT_CRYPTO_TAG_UID](js-apis-huksExternalCrypto.md#huksexternalcryptotag) parameter.|

**Return value**

| Type  | Description |
| -------- | ------- |
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise used to return the result. If the call is successful, **resultCode** is **0**, and the **authState** of **HuksCryptoExtensionResult** contains the obtained PIN authentication state. If the call fails, **resultCode** contains the error code.<br>Possible error code values:<br>34800000 Key extension error.<br>34800002 UKey driver error.<br>34800004 Handle does not exist.<br>34800005 The handle is unavailable.<br>For details, see [HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode).|

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
    return Promise.resolve(result);
  }
}
```

### onClearUkeyPinAuthState

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
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise used to return the result. If the call is successful, **resultCode** is **0**, indicating that the PIN authentication state is cleared successfully. If the call fails, **resultCode** contains the error code.<br>Possible error code values:<br>34800000 Key extension error.<br>34800002 UKey driver error.<br>34800004 Handle does not exist.<br>34800005 The handle is unavailable.<br>For details, see [HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode).|

**Example**

```ts
import { huksExternalCrypto, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onClearUkeyPinAuthState(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
    const result: HuksCryptoExtensionResult = {
      resultCode: 0
    };

    // ...
    return Promise.resolve(result);
  }
}
```

### onInitSession

onInitSession(handle: string, params: huks.HuksOptions): Promise\<HuksCryptoExtensionResult>

Initializes a key session. (The first operation of the Init-Update-Finish process.) This API uses a promise to return the result.

**System capability**: SystemCapability.Security.Huks.CryptoExtension

**Parameters**

| Name  | Type| Mandatory| Description|
| -------- | ----- | ---- | ------- |
| handle | string                      | Yes  | Resource handle.|
| params  | [huks.HuksOptions](js-apis-huks.md#huksoptions)  | Yes  | Input parameters. The application is identified by the [HUKS_EXT_CRYPTO_TAG_UID](js-apis-huksExternalCrypto.md#huksexternalcryptotag) parameter.|

**Return value**

| Type| Description|
| --------- | ---------|
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise used to return the result. If the call is successful, **resultCode** is **0** and **handle** is not empty. If the call fails, **resultCode** contains the error code.<br>Possible error code values:<br>34800000 Key extension error.<br>34800002 UKey driver error.<br>34800003 The UKey PIN is not authenticated.<br>34800004 Handle does not exist.<br>34800005 The handle is unavailable.<br>34800007 The UKey PIN is locked.<br>For details, see [HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode).|

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
    return Promise.resolve(result);
  }
}
```

### onUpdateSession

onUpdateSession(initHandle: string, params: huks.HuksOptions): Promise\<HuksCryptoExtensionResult>

Updates a key session. (The second operation of the Init-Update-Finish process.) This API uses a promise to return the result.

**System capability**: SystemCapability.Security.Huks.CryptoExtension

**Parameters**

| Name  | Type | Mandatory| Description|
| -------- | ----- | ---- | ------|
| initHandle | string | Yes  | Resource handle.  |
| params  | [huks.HuksOptions](js-apis-huks.md#huksoptions)  | Yes  | Input parameters. The application is identified by the [HUKS_EXT_CRYPTO_TAG_UID](js-apis-huksExternalCrypto.md#huksexternalcryptotag) parameter.|

**Return value**

| Type| Description|
| --------- | ---------|
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise used to return the result. If the call is successful, **resultCode** is **0**. If the call fails, **resultCode** contains the error code.<br>Possible error code values:<br>34800000 Key extension error.<br>34800002 UKey driver error.<br>34800003 The UKey PIN is not authenticated.<br>34800004 Handle does not exist.<br>34800005 The handle is unavailable.<br>34800007 The UKey PIN is locked.<br>For details, see [HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode).|

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
    return Promise.resolve(result);
  }
}
```

### onFinishSession

onFinishSession(initHandle: string, params: huks.HuksOptions): Promise\<HuksCryptoExtensionResult>

Ends a key session. (The last operation of the Init-Update-Finish process.) This API uses a promise to return the result.

**System capability**: SystemCapability.Security.Huks.CryptoExtension

**Parameters**

| Name  | Type| Mandatory| Description |
| -------- | -------- | ---- | --------- |
| initHandle | string  | Yes  | Resource handle.|
| params  | [huks.HuksOptions](js-apis-huks.md#huksoptions)  | Yes  | Input parameters. The application is identified by the [HUKS_EXT_CRYPTO_TAG_UID](js-apis-huksExternalCrypto.md#huksexternalcryptotag) parameter, and the algorithm parameters (such as the algorithm type and padding mode) are also included.|

**Return value**

| Type| Description|
| ------- | ---------- |
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise used to return the result. If the call is successful, **resultCode** is **0**. If the call fails, **resultCode** contains the error code.<br>Possible error code values:<br>34800000 Key extension error.<br>34800002 UKey driver error.<br>34800003 The UKey PIN is not authenticated.<br>34800004 Handle does not exist.<br>34800005 The handle is unavailable.<br>34800007 The UKey PIN is locked.<br>For details, see [HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode).|

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
    return Promise.resolve(result);
  }
}
```

### onExportCertificate

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
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise used to return the result. If the call is successful, **certs** contains the single certificate obtained. If the call fails, **resultCode** contains the error code.<br>Possible error code values:<br>34800000 Key extension error.<br>34800001 The UKey does not exist.<br>34800002 UKey driver error.<br>34800004 Handle does not exist.<br>For details, see [HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode).|

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
    return Promise.resolve(result);
  }
}
```

### onEnumCertificates

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
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise used to return the result. If the call is successful, **certs** contains all the obtained certificates. If the call fails, **resultCode** contains the error code.<br>Possible error code values:<br>34800000 Key extension error.<br>34800001 The UKey does not exist.<br>34800002 UKey driver error.<br>For details, see [HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode).|

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
    return Promise.resolve(result);
  }
}
```

### onGetResourceId

onGetResourceId(params: huksExternalCrypto.HuksExternalCryptoParam[]):Promise&lt;HuksCryptoExtensionResult&gt;

Obtains the resource ID of an external extension device. This API uses a promise to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Security.Huks.CryptoExtension

**Parameters**

| Name  | Type| Mandatory| Description|
| -------- | --------- | ---- | -------- |
| params  | [huksExternalCrypto.HuksExternalCryptoParam](js-apis-huksExternalCrypto.md#huksexternalcryptoparam)[] | Yes  | Property parameters required for obtaining the resource ID. Mandatory tags include [HUKS_EXT_CRYPTO_TAG_RESOURCE_INFO](js-apis-huksExternalCrypto.md#huksexternalcryptotag) (vendor-defined resource information) and [HUKS_EXT_CRYPTO_TAG_UID](js-apis-huksExternalCrypto.md#huksexternalcryptotag) (caller identity).|

**Return value**

| Type| Description|
| ---------- | ----------- |
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise used to return the result. If the call is successful, **resultCode** is **0** and **resourceId** contains the resource ID. If the call fails, **resultCode** contains the error code.<br>Possible error code values:<br>34800000 Key extension error.<br>For details, see [HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode).|

**Example**

```ts
import { huksExternalCrypto, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onGetResourceId(params: huksExternalCrypto.HuksExternalCryptoParam[]): Promise<HuksCryptoExtensionResult> {
    const result: HuksCryptoExtensionResult = {
      resultCode: 0,
      resourceId: "test resourceId"
    };

    // ...
    return Promise.resolve(result);
  }
}
```

### onImportCertificate

onImportCertificate(handle: string, params: huksExternalCrypto.HuksExternalCryptoParam[], certInfo: HuksCryptoExtensionCertInfo): Promise&lt;HuksCryptoExtensionResult&gt;

Imports the certificate of a specified resource handle. This API uses a promise to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Security.Huks.CryptoExtension

**Parameters**

| Name  | Type | Mandatory| Description |
| -------- | ----- | ---- | ------|
| handle | string | Yes  | Resource handle of the certificate to be imported.|
| params  | [huksExternalCrypto.HuksExternalCryptoParam](js-apis-huksExternalCrypto.md#huksexternalcryptoparam)[] | Yes| Property parameters required for importing the certificate.|
| certInfo | [HuksCryptoExtensionCertInfo](#hukscryptoextensioncertinfo) | Yes  | Information about the certificate to be imported. The certificate type (**purpose**) must be specified.|

**Return value**

| Type   | Description  |
| -------- | -----------|
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise used to return the result. If the call is successful, the value of **resultCode** is **0**, indicating that the certificate is imported successfully. If the call fails, **resultCode** contains the error code information, and **errInfo** contains the detailed error information.<br>Possible error code values:<br>34800000 Key extension error.<br>34800001 The UKey does not exist.<br>34800002 UKey driver error.<br>34800004 Handle does not exist.<br>34800005 The handle is unavailable.<br>For details, see [HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode).|

**Example**

```ts
import { huksExternalCrypto, CryptoExtensionAbility, HuksCryptoExtensionResult,
  HuksCryptoExtensionCertInfo } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onImportCertificate(handle: string, params: huksExternalCrypto.HuksExternalCryptoParam[],
      certInfo: HuksCryptoExtensionCertInfo): Promise<HuksCryptoExtensionResult> {
    const result: HuksCryptoExtensionResult = {
      resultCode: 0
    };

    // ...
    return Promise.resolve(result);
  }
}
```

### onGenerateKeyItem

onGenerateKeyItem(handle: string, params: huks.HuksParam[]): Promise&lt;HuksCryptoExtensionResult&gt;

Generates a key pair in the extension device. This API uses a promise to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Security.Huks.CryptoExtension

**Parameters**

| Name  | Type | Mandatory| Description |
| -------- | ----- | ---- | ------|
| handle | string | Yes  | Resource handle of the key to be generated.|
| params  | [huks.HuksParam](js-apis-huks.md#huksparam)[] | Yes| Property parameters of the key generation operation. Mandatory tag: [HUKS_EXT_CRYPTO_TAG_UID](js-apis-huksExternalCrypto.md#huksexternalcryptotag) (identity of the caller).|

**Return value**

| Type   | Description  |
| -------- | -----------|
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise used to return the result. If the call is successful, **resultCode** is **0**, indicating that the key is generated successfully. If the call fails, **resultCode** contains the error code.<br>Possible error code values:<br>34800000 Key extension error.<br>**34800002**: Ukey driver error.<br>34800004 Handle does not exist.<br>34800005 The handle is unavailable.<br>For details, see [HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode).|

**Example**

```ts
import { huks, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onGenerateKeyItem(handle: string, params: huks.HuksParam[]): Promise<HuksCryptoExtensionResult> {
    // Parse optional parameters.
    let algorithm: huks.HuksKeyAlg | undefined = params.find(
      param => param.tag === huks.HuksTag.HUKS_TAG_ALGORITHM)?.value as huks.HuksKeyAlg;
    let keySize: huks.HuksKeySize | undefined = params.find(
      param => param.tag === huks.HuksTag.HUKS_TAG_KEY_SIZE)?.value as huks.HuksKeySize;
    let purpose: huks.HuksKeyPurpose | undefined = params.find(
      param => param.tag === huks.HuksTag.HUKS_TAG_PURPOSE)?.value as huks.HuksKeyPurpose;

    // If there is no input parameter, set the default value.
    if (algorithm === undefined) {
      algorithm = huks.HuksKeyAlg.HUKS_ALG_RSA; // RSA is used by default.
    }
    if (keySize === undefined) {
      keySize = huks.HuksKeySize.HUKS_RSA_KEY_SIZE_2048; // The default value is 2048 bits.
    }
    if (purpose === undefined) {
      purpose = huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_SIGN; // The default purpose is signing.
    }

    const result: HuksCryptoExtensionResult = {
      resultCode: 0
    };

    // ...
    return Promise.resolve(result);
  }
}
```

### onExportKeyItem

onExportKeyItem(handle: string, params: huks.HuksParam[]): Promise&lt;HuksCryptoExtensionResult&gt;

Exports the public key of a specified key. This API uses a promise to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Security.Huks.CryptoExtension

**Parameters**

| Name  | Type | Mandatory| Description |
| -------- | ----- | ---- | ------|
| handle | string | Yes  | Resource handle of the public key to be exported.|
| params  | [huks.HuksParam](js-apis-huks.md#huksparam)[] | Yes| Property parameters of the operation for exporting the public key. Mandatory tag: [HUKS_EXT_CRYPTO_TAG_UID](js-apis-huksExternalCrypto.md#huksexternalcryptotag) (identity of the caller).|

**Return value**

| Type   | Description  |
| -------- | -----------|
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise used to return the result. If the call is successful, the value of **resultCode** is **0**, and **outData** contains the exported public key. If the call fails, **resultCode** contains the error code information, and **errInfo** contains the detailed error information.<br>Possible error code values:<br>34800000 Key extension error.<br>**34800002**: Ukey driver error.<br>34800004 Handle does not exist.<br>34800005 The handle is unavailable.<br>For details, see [HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode).|

**Example**

```ts
import { huks, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onExportKeyItem(handle: string, params: huks.HuksParam[]): Promise<HuksCryptoExtensionResult> {
    // Parse the optional parameters. It is recommended that the key purpose be passed.
    let purpose: huks.HuksKeyPurpose | undefined = params.find(
      param => param.tag === huks.HuksTag.HUKS_TAG_PURPOSE)?.value as huks.HuksKeyPurpose;

    // If the purpose parameter is not passed, set the default value. (The default signing purpose is recommended.)
    if (purpose === undefined) {
      purpose = huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_SIGN;
    }

    let pubKey: Uint8Array = new Uint8Array(1024);
    const result: HuksCryptoExtensionResult = {
      resultCode: 0,
      outData: pubKey
    };

    // ...
    return Promise.resolve(result);
  }
}
```

### onImportWrappedKeyItem

onImportWrappedKeyItem(handle: string, wrappedHandle: string, params: huks.HuksParam[], wrappedKey: Uint8Array): Promise&lt;HuksCryptoExtensionResult&gt;

Imports the encrypted and encapsulated key pair. This API uses a promise to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Security.Huks.CryptoExtension

**Parameters**

| Name  | Type | Mandatory| Description |
| -------- | ----- | ---- | ------|
| handle | string | Yes  | Handle to the resource whose key is to be imported.|
| wrappedHandle | string | Yes  | Handle to the key resource used to decapsulate the imported key.|
| params  | [huks.HuksParam](js-apis-huks.md#huksparam)[] | Yes| Property parameters for the operation of importing an encapsulated key. Mandatory tag: [HUKS_EXT_CRYPTO_TAG_UID](js-apis-huksExternalCrypto.md#huksexternalcryptotag) (identity of the caller).|
| wrappedKey | Uint8Array | Yes  | Encapsulated key data. The format is defined by key extension.|

**Return value**

| Type   | Description  |
| -------- | -----------|
| Promise\<[HuksCryptoExtensionResult](#hukscryptoextensionresult)> | Promise used to return the result. If the call is successful, **resultCode** is **0**, indicating that the key is imported successfully. If the call fails, **resultCode** contains the error code information, and **errInfo** contains the detailed error information.<br>Possible error code values:<br>34800000 Key extension error.<br>**34800002**: Ukey driver error.<br>34800004 Handle does not exist.<br>34800005 The handle is unavailable.<br>For details, see [HuksCryptoExtensionResultCode](#hukscryptoextensionresultcode).|

**Example**

```ts
import { huks, CryptoExtensionAbility, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

export default class CryptoExtension extends CryptoExtensionAbility {
  onImportWrappedKeyItem(handle: string, wrappedHandle: string, params: huks.HuksParam[],
      wrappedKey: Uint8Array): Promise<HuksCryptoExtensionResult> {
    // Parse optional parameters.
    let algorithm: huks.HuksKeyAlg | undefined = params.find(
      param => param.tag === huks.HuksTag.HUKS_TAG_ALGORITHM)?.value as huks.HuksKeyAlg;
    let keySize: huks.HuksKeySize | undefined = params.find(
      param => param.tag === huks.HuksTag.HUKS_TAG_KEY_SIZE)?.value as huks.HuksKeySize;
    let purpose: huks.HuksKeyPurpose | undefined = params.find(
      param => param.tag === huks.HuksTag.HUKS_TAG_PURPOSE)?.value as huks.HuksKeyPurpose;

    // If there is no input parameter, set the default value.
    if (algorithm === undefined) {
      algorithm = huks.HuksKeyAlg.HUKS_ALG_RSA;
    }
    if (keySize === undefined) {
      keySize = huks.HuksKeySize.HUKS_RSA_KEY_SIZE_2048;
    }
    if (purpose === undefined) {
      purpose = huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT;
    }

    const result: HuksCryptoExtensionResult = {
      resultCode: 0
    };

    // ...
    return Promise.resolve(result);
  }
}
```
