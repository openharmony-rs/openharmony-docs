# @ohos.security.certManager (Certificate Management) (System API)

<!--Kit: Device Certificate Kit-->
<!--Subsystem: Security-->
<!--Owner: @chaceli-->
<!--Designer: @chande-->
<!--Tester: @zhangzhi1995-->
<!--Adviser: @zengyawen-->

The **certManager** module provides system-level certificate management capabilities to implement management and secure use of certificates throughout their lifecycle (installation, storage, use, and destruction).

> **NOTE**
>
> - The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - This topic describes only the system APIs provided by the module. For details about its public APIs, see [@ohos.security.certManager (Certificate Management)](js-apis-certManager.md).

## Modules to Import

```ts
import { certificateManager } from '@kit.DeviceCertificateKit';
```

## CMErrorCode

Enumerates the error codes used in the certificate management APIs.

**System capability**: System SystemCapability.Security.CertificateManager

| Name      | Value|  Description     |
| ---------- | ------ | --------- |
| CM_ERROR_NOT_SYSTEM_APP   | 202      | The caller is not a system application.<br> **System API**: This is a system API.|
| CM_ERROR_PASSWORD_IS_ERR   | 17500008      | The password is incorrect.<br> **System API**: This is a system API.<br>**Since**: 26.0.0|

## certificateManager.getAllAppPrivateCertificates

getAllAppPrivateCertificates(callback: AsyncCallback\<CMResult>): void

Obtains all private credentials. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.ACCESS_CERT_MANAGER and ohos.permission.ACCESS_CERT_MANAGER_INTERNAL

**System capability**: System SystemCapability.Security.CertificateManager

**System API**: This is a system API.

**Parameters**

| Name  | Type                                                       | Mandatory| Description                                                        |
| -------- | ----------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| callback | AsyncCallback\<[CMResult](js-apis-certManager.md#cmresult)> | Yes  | Callback used to return the result. If all private credentials are obtained, **err** is **null**, and **data** is the **credentialList** attribute in the [CMResult](js-apis-certManager.md#cmresult) object. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Certificate Management Error Codes](errorcode-certManager.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 17500001 | Internal error. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error. |

**Example**
```ts
import { certificateManager } from '@kit.DeviceCertificateKit';

try {
  certificateManager.getAllAppPrivateCertificates((err, cmResult) => {
    if (err != null) {
      console.error(`Failed to get all app private certificates. Code: ${err.code}, message: ${err.message}`);
    } else {
      if (cmResult === undefined) { // If the number of private credentials is 0, return undefined in cmResult.
        console.info('The count of the app private certificates is 0.');
      } else if (cmResult.credentialList == undefined) {
        console.info('The result of getting all app private certificates is undefined.');
      } else {
        let list = cmResult.credentialList;
        console.info('Succeeded in getting all app private certificates.');
      }
    }
  });
} catch (error) {
  console.error(`Failed to get all app private certificates. Code: ${error.code}, message: ${error.message}`);
}
```

## certificateManager.getAllAppPrivateCertificates

getAllAppPrivateCertificates(): Promise\<CMResult>

Obtains all private credentials. This API uses a promise to return the result.

**Required permissions**: ohos.permission.ACCESS_CERT_MANAGER and ohos.permission.ACCESS_CERT_MANAGER_INTERNAL

**System capability**: System SystemCapability.Security.CertificateManager

**System API**: This is a system API.

**Return value**

| Type                                                 | Description                                                        |
| ----------------------------------------------------- | ------------------------------------------------------------ |
| Promise\<[CMResult](js-apis-certManager.md#cmresult)> | Promise used to return the result, which is the value of **credentialList** in the [CMResult](js-apis-certManager.md#cmresult) object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Certificate Management Error Codes](errorcode-certManager.md).

| ID| Error Message     |
| -------- | ------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 17500001 | Internal error. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error. |

**Example**
```ts
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  certificateManager.getAllAppPrivateCertificates().then((cmResult) => {
    if (cmResult === undefined) { // If the number of private credentials is 0, return undefined in cmResult.
      console.info('The count of the app private certificates is 0.');
    } else if (cmResult.credentialList == undefined) {
      console.info('The result of getting all app private certificates is undefined.');
    } else {
      let list = cmResult.credentialList;
      console.info('Succeeded in getting all app private certificates.');
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to get all app private certificates. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error) {
  console.error(`Failed to get all app private certificates. Code: ${error.code}, message: ${error.message}`);
}
```

## certificateManager.getAllSystemAppCertificates<sup>12+</sup>

getAllSystemAppCertificates(): Promise\<CMResult>

Obtains all system credentials. This API uses a promise to return the result.

**Required permissions**: ohos.permission.ACCESS_CERT_MANAGER

**System capability**: System SystemCapability.Security.CertificateManager

**System API**: This is a system API.

**Return value**

| Type                                                 | Description                                                        |
| ----------------------------------------------------- | ------------------------------------------------------------ |
| Promise\<[CMResult](js-apis-certManager.md#cmresult)> | Promise used to return the result, which is the value of **credentialList** in the [CMResult](js-apis-certManager.md#cmresult) object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Certificate Management Error Codes](errorcode-certManager.md).

| ID| Error Message     |
| -------- | ------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 17500001 | Internal error. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error. |

**Example**
```ts
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  certificateManager.getAllSystemAppCertificates().then((cmResult) => {
    if (cmResult === undefined) { // If the number of system credentials is 0, return undefined in cmResult.
      console.info('The count of the system certificates is 0.');
    } else if (cmResult.credentialList == undefined) {
      console.info('The result of getting all system app certificates is undefined.');
    } else {
      let list = cmResult.credentialList;
      console.info('Succeeded in getting all system app certificates.');
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to get all system app certificates. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error) {
  console.error(`Failed to get all system app certificates. Code: ${error.code}, message: ${error.message}`);
}
```

## certificateManager.getSystemTrustedCertificate

getSystemTrustedCertificate(certUri: string): Promise\<CMResult>

Obtains details about a CA certificate trusted by the system. This API is called only by the certificate management application. This API uses a promise to return the result.

**Required permissions**: ohos.permission.ACCESS_CERT_MANAGER and ohos.permission.ACCESS_CERT_MANAGER_INTERNAL

**System capability**: System SystemCapability.Security.CertificateManager

**System API**: This is a system API.

**Since**: 26.0.0

**Parameters**

| Name  | Type                                             | Mandatory| Description                      |
| -------- | ------------------------------------------------- | ---- | -------------------------- |
| certUri | string                   | Yes  | Unique identifier of the certificate. You can obtain the value through [getSystemTrustedCertificateList](#certificatemanagergetsystemtrustedcertificatelist).|

**Return value**

| Type                           | Description                                                        |
| ------------------------------- | ------------------------------------------------------------ |
| Promise\<[CMResult](js-apis-certManager.md#cmresult)> | Promise used to return the operation result, that is, **certInfo** in the [CMResult](js-apis-certManager.md#cmresult) object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Certificate Management Error Codes](errorcode-certManager.md).

| ID| Error Message     |
| -------- | ------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 401 | Parameter verification failed. Possible causes: the URI is null or the URI format is wrong. |
| 17500001 | Internal error. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error. Please try again. |
| 17500002 | The certificate does not exist. |

**Example**
```ts
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

let certUri: string = 'test'; /* Unique identifier of the certificate, which can be obtained through the getSystemTrustedCertificateList API. */
try {
  certificateManager.getSystemTrustedCertificate(certUri).then((cmResult: certificateManager.CMResult) => {
    if (cmResult?.certInfo == undefined) {
      console.info('The result of getting system trusted certificate is undefined.');
    } else {
      let cert: certificateManager.CertInfo = cmResult.certInfo;
      console.info('Succeeded in getting system trusted certificate.');
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to get system trusted certificate. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error: BusinessError) {
  console.error(`Failed to get system trusted certificate. Code: ${error.code}, message: ${error.message}`);
}
```

## certificateManager.getSystemTrustedCertificateList

getSystemTrustedCertificateList(): Promise\<CMResult>

Obtains the list of CA certificates trusted by the system. This API is called only by the certificate management application. This API uses a promise to return the result.

**Required permissions**: ohos.permission.ACCESS_CERT_MANAGER and ohos.permission.ACCESS_CERT_MANAGER_INTERNAL

**System capability**: System SystemCapability.Security.CertificateManager

**System API**: This is a system API.

**Since**: 26.0.0

**Return value**

| Type                           | Description                                                        |
| ------------------------------- | ------------------------------------------------------------ |
| Promise\<[CMResult](js-apis-certManager.md#cmresult)> | Promise used to return the operation result, that is, **certList** in the [CMResult](js-apis-certManager.md#cmresult) object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Certificate Management Error Codes](errorcode-certManager.md).

| ID| Error Message     |
| -------- | ------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 17500001 | Internal error. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error. Please try again. |

**Example**
```ts
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  certificateManager.getSystemTrustedCertificateList().then((cmResult: certificateManager.CMResult) => {
    if (cmResult === undefined) { // If the number of trusted CA certificates is 0, the returned cmResult is undefined.
      console.info('The count of system trusted certificates is 0.');
    } else if (cmResult.certList == undefined) {
      console.info('The result of getting system trusted certificates is undefined.');
    } else {
      let list: Array<certificateManager.CertAbstract> = cmResult.certList;
      console.info('Succeeded in getting system trusted certificates.');
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to get system trusted certificates. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error: BusinessError) {
  console.error(`Failed to get system trusted certificates. Code: ${error.code}, message: ${error.message}`);
}
```

## certificateManager.setCertificateStatus

setCertificateStatus(certUri: string, certType: CertType, enabled: boolean) : Promise\<void>

Sets the status of a CA certificate. Currently, only the status of a user's CA certificate can be set. This API is called only by the certificate management application. This API uses a promise to return the result.

**Required permissions**: ohos.permission.ACCESS_CERT_MANAGER and ohos.permission.ACCESS_USER_TRUSTED_CERT

**System capability**: System SystemCapability.Security.CertificateManager

**System API**: This is a system API.

**Since**: 26.0.0

**Parameters**

| Name  | Type                                             | Mandatory| Description                      |
| -------- | ------------------------------------------------- | ---- | -------------------------- |
| certUri | string                   | Yes  | Unique identifier of the certificate. Currently, only user CA certificates are supported.|
| certType | [CertType](js-apis-certManager.md#certtype18) | Yes  | Certificate type. Currently, only the status of user CA certificates (**CA_CERT_USER**) can be set.|
| enabled | boolean                   | Yes  | Whether the certificate is enabled. **true**: enabled; **false**: disabled.|

**Return value**

| Type                           | Description                                                        |
| ------------------------------- | ------------------------------------------------------------ |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Certificate Management Error Codes](errorcode-certManager.md).

| ID| Error Message     |
| -------- | ------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 401 | Parameter verification failed. Possible causes: the URI is null or the URI format is wrong, the certType's value is invalid or not supported. |
| 17500001 | Internal error. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error. Please try again. |
| 17500002 | The certificate does not exist. |

**Example**
```ts
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

let certUri: string = 'test'; /* Unique identifier of the user CA certificate. */
try {
  /* Set the user CA certificate status to enabled. */
  certificateManager.setCertificateStatus(certUri, certificateManager.CertType.CA_CERT_USER, true).then(() => {
    console.info('Succeeded in setting certificate status.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to set certificate status. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error: BusinessError) {
  console.error(`Failed to set certificate status. Code: ${error.code}, message: ${error.message}`);
}
```

## certificateManager.uninstallAllUserTrustedCertificate

uninstallAllUserTrustedCertificate() : Promise\<void>

Uninstalls all CA certificates trusted by the user. This API is called only by the certificate management application. This API uses a promise to return the result.

**Required permissions**: ohos.permission.ACCESS_CERT_MANAGER and ohos.permission.ACCESS_USER_TRUSTED_CERT

**System capability**: System SystemCapability.Security.CertificateManager

**System API**: This is a system API.

**Since**: 26.0.0

**Return value**

| Type                           | Description                                                        |
| ------------------------------- | ------------------------------------------------------------ |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Certificate Management Error Codes](errorcode-certManager.md).

| ID| Error Message     |
| -------- | ------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 17500001 | Internal error. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error. Please try again. |

**Example**
```ts
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  certificateManager.uninstallAllUserTrustedCertificate().then(() => {
    console.info('Succeeded in uninstalling all user trusted certificates.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to uninstall all user trusted certificates. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error: BusinessError) {
  console.error(`Failed to uninstall all user trusted certificates. Code: ${error.code}, message: ${error.message}`);
}
```

## certificateManager.installPublicCertificate

installPublicCertificate(keystore: Uint8Array, keystorePwd: string) : Promise\<CMResult>

Installs the public credential of the user. This API is called only by the certificate management application. This API uses a promise to return the result.

**Required permissions**: ohos.permission.ACCESS_CERT_MANAGER and ohos.permission.ACCESS_CERT_MANAGER_INTERNAL

**System capability**: System SystemCapability.Security.CertificateManager

**System API**: This is a system API.

**Since**: 26.0.0

**Parameters**

| Name     | Type      | Mandatory|Description                                           |
| ----------- | ---------- | ---- |---------------------------------------------------|
| keystore    | Uint8Array | Yes |Keystore file containing the key pair and certificate. Only the P12 format is supported.|
| keystorePwd | string     | Yes |Password of the keystore file.|

**Return value**

| Type                           | Description                                                        |
| ------------------------------- | ------------------------------------------------------------ |
| Promise\<[CMResult](js-apis-certManager.md#cmresult)> | Promise used to return the operation result, that is, **uri** in the [CMResult](js-apis-certManager.md#cmresult) object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Certificate Management Error Codes](errorcode-certManager.md).

| ID   | Error Message                                                                                                                                           |
| ----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| 201                    | Permission verification failed. The application does not have the permission required to call the API. |
| 202                    | Permission verification failed. A non-system application calls a system API. |
| 401                    | Parameter verification failed. Possible causes: the keystore parameter is empty or exceeds the maximum length. |
| 17500001               | Internal error. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error. Please try again. |
| 17500003               | Indicates that the certificate is in an invalid format. |
| 17500004               | Indicates that the number of certificates reaches the maximum allowed. |
| 17500008               | Indicates that the password is error. |

**Example**

```ts
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

/* The data of the credential to be installed must be assigned based on the service. The data in this example is not the real credential data. */
let keystore: Uint8Array = new Uint8Array([
    0x30, 0x82, 0x0b, 0xc1, 0x02, 0x01,
]);
let keystorePwd: string = "123456";
try {
    certificateManager.installPublicCertificate(keystore, keystorePwd).then((cmResult: certificateManager.CMResult) => {
        let uri: string = (cmResult?.uri == undefined) ? '' : cmResult.uri;
        console.info('Succeeded in installing public certificate.');
    }).catch((err: BusinessError) => {
        console.error(`Failed to install public certificate. Code: ${err.code}, message: ${err.message}`);
    })
} catch (error: BusinessError) {
    console.error(`Failed to install public certificate. Code: ${error.code}, message: ${error.message}`);
}
```

## certificateManager.uninstallPublicCertificate

uninstallPublicCertificate(keyUri: string) : Promise\<void>

Uninstalls the public credential of the user. This API is called only by the certificate management application. This API uses a promise to return the result.

**Required permissions**: ohos.permission.ACCESS_CERT_MANAGER and ohos.permission.ACCESS_CERT_MANAGER_INTERNAL

**System capability**: System SystemCapability.Security.CertificateManager

**System API**: This is a system API.

**Since**: 26.0.0

**Parameters**

| Name  | Type                                             | Mandatory| Description                      |
| -------- | ------------------------------------------------- | ---- | -------------------------- |
| keyUri | string                   | Yes  | Unique identifier of a user's public credential.|

**Return value**

| Type                           | Description                                                        |
| ------------------------------- | ------------------------------------------------------------ |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Certificate Management Error Codes](errorcode-certManager.md).

| ID   | Error Message                                                                                                                                           |
| ----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| 201                    | Permission verification failed. The application does not have the permission required to call the API. |
| 202                    | Permission verification failed. A non-system application calls a system API. |
| 401                    | Parameter verification failed. Possible causes: the URI is null or the URI format is wrong. |
| 17500001               | Internal error. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error. Please try again. |
| 17500002               | Indicates that the certificate does not exist. |

**Example**

```ts
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

let keyUri: string = 'test'; /* Unique identifier of the user public credential. */
try {
    certificateManager.uninstallPublicCertificate(keyUri).then(() => {
        console.info('Succeeded in uninstalling public certificate.');
    }).catch((err: BusinessError) => {
        console.error(`Failed to uninstall public certificate. Code: ${err.code}, message: ${err.message}`);
    })
} catch (error: BusinessError) {
    console.error(`Failed to uninstall public certificate. Code: ${error.code}, message: ${error.message}`);
}
```

## certificateManager.getAllPublicCertificates

getAllPublicCertificates() : Promise\<CMResult>

Obtains the public credentials of all users. This API is called only by the certificate management application. This API uses a promise to return the result.

**Required permissions**: ohos.permission.ACCESS_CERT_MANAGER and ohos.permission.ACCESS_CERT_MANAGER_INTERNAL

**System capability**: System SystemCapability.Security.CertificateManager

**System API**: This is a system API.

**Since**: 26.0.0

**Return value**

| Type                           | Description                                                        |
| ------------------------------- | ------------------------------------------------------------ |
| Promise\<[CMResult](js-apis-certManager.md#cmresult)> | Promise used to return the operation result, that is, **credentialDetailList** in the [CMResult](js-apis-certManager.md#cmresult) object.<br>Note: If the number of public credentials is 0, the value of **CMResult** is **undefined**.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Certificate Management Error Codes](errorcode-certManager.md).

| ID   | Error Message                                                                                                                                           |
| ----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| 201                    | Permission verification failed. The application does not have the permission required to call the API. |
| 202                    | Permission verification failed. A non-system application calls a system API. |
| 17500001               | Internal error. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error. Please try again. |

**Example**

```ts
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
    certificateManager.getAllPublicCertificates().then((cmResult: certificateManager.CMResult) => {
        if (cmResult === undefined) { // If the number of public credentials is 0, return undefined in cmResult.
            console.info('The count of public certificates is 0.');
        } else if (cmResult.credentialDetailList == undefined) {
            console.info('The result of getting all public certificates is undefined.');
        } else {
            let list: Array<certificateManager.Credential> = cmResult.credentialDetailList;
            console.info('Succeeded in getting all public certificates.');
        }
    }).catch((err: BusinessError) => {
        console.error(`Failed to get all public certificates. Code: ${err.code}, message: ${err.message}`);
    })
} catch (error: BusinessError) {
    console.error(`Failed to get all public certificates. Code: ${error.code}, message: ${error.message}`);
}
```

## certificateManager.grantPublicCertificate

grantPublicCertificate(keyUri: string, clientAppUid: number) : Promise\<CMResult>

Grants the permission for an application to use the public credentials of a user. This API is called only by the certificate management application. This API uses a promise to return the result.

**Required permissions**: ohos.permission.ACCESS_CERT_MANAGER and ohos.permission.ACCESS_CERT_MANAGER_INTERNAL

**System capability**: System SystemCapability.Security.CertificateManager

**System API**: This is a system API.

**Since**: 26.0.0

**Parameters**

| Name      | Type      | Mandatory|Description                                           |
| ------------ | ---------- | ---- |---------------------------------------------------|
| keyUri       | string     | Yes |Unique identifier of a user's public credential.|
| clientAppUid | number        | Yes |Application UID.|

**Return value**

| Type                           | Description                                                        |
| ------------------------------- | ------------------------------------------------------------ |
| Promise\<[CMResult](js-apis-certManager.md#cmresult)> | Promise used to return the operation result, that is, **uri** in the [CMResult](js-apis-certManager.md#cmresult) object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Certificate Management Error Codes](errorcode-certManager.md).

| ID   | Error Message                                                                                                                                           |
| ----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| 201                    | Permission verification failed. The application does not have the permission required to call the API. |
| 202                    | Permission verification failed. A non-system application calls a system API. |
| 401                    | Parameter verification failed. Possible causes: the URI is null or the URI format is wrong. |
| 17500001               | Internal error. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error. Please try again. |
| 17500002               | Indicates that the certificate does not exist. |

**Example**

```ts
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

let keyUri: string = 'test'; /* Unique identifier of the user public credential. */
let clientAppUid: number = 1001; /* Application UID */
try {
    certificateManager.grantPublicCertificate(keyUri, clientAppUid).then((cmResult: certificateManager.CMResult) => {
        let uri: string = (cmResult?.uri == undefined) ? '' : cmResult.uri;
        console.info('Succeeded in granting public certificate.');
    }).catch((err: BusinessError) => {
        console.error(`Failed to grant public certificate. Code: ${err.code}, message: ${err.message}`);
    })
} catch (error: BusinessError) {
    console.error(`Failed to grant public certificate. Code: ${error.code}, message: ${error.message}`);
}
```

## certificateManager.getAuthorizedAppList

getAuthorizedAppList(keyUri: string) : Promise\<CMResult>

Obtains the list of authorized applications of a user's public credential. This API is called only by the certificate management application. This API uses a promise to return the result.

**Required permissions**: ohos.permission.ACCESS_CERT_MANAGER and ohos.permission.ACCESS_CERT_MANAGER_INTERNAL

**System capability**: System SystemCapability.Security.CertificateManager

**System API**: This is a system API.

**Since**: 26.0.0

**Parameters**

| Name  | Type                                             | Mandatory| Description                      |
| -------- | ------------------------------------------------- | ---- | -------------------------- |
| keyUri | string                   | Yes  | Unique identifier of a user's public credential.|

**Return value**

| Type                           | Description                                                        |
| ------------------------------- | ------------------------------------------------------------ |
| Promise\<[CMResult](js-apis-certManager.md#cmresult)> | Promise used to return the result, which is the value of **appUidList** in the [CMResult](js-apis-certManager.md#cmresult) object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Certificate Management Error Codes](errorcode-certManager.md).

| ID   | Error Message                                                                                                                                           |
| ----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| 201                    | Permission verification failed. The application does not have the permission required to call the API. |
| 202                    | Permission verification failed. A non-system application calls a system API. |
| 401                    | Parameter verification failed. Possible causes: the URI is null or the URI format is wrong. |
| 17500001               | Internal error. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error. Please try again. |
| 17500002               | Indicates that the certificate does not exist. |

**Example**

```ts
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

let keyUri: string = 'test'; /* Unique identifier of the user public credential. */
try {
     certificateManager.getAuthorizedAppList(keyUri).then((cmResult: certificateManager.CMResult) => {
        if (cmResult?.appUidList == undefined) {
            console.info('The result of getting authorized app list is undefined.');
        } else {
            let appUidList: Array<string> = cmResult.appUidList;
            console.info('Succeeded in getting authorized app list.');
        }
    }).catch((err: BusinessError) => {
        console.error(`Failed to get authorized app list. Code: ${err.code}, message: ${err.message}`);
    })
} catch (error: BusinessError) {
    console.error(`Failed to get authorized app list. Code: ${error.code}, message: ${error.message}`);
}
```

## certificateManager.removeGrantedPublicCertificate

removeGrantedPublicCertificate(keyUri: string, clientAppUid: number) : Promise\<void>

Removes the permission for an application to use the public credentials of a user. This API is called only by the certificate management application. This API uses a promise to return the result.

**Required permissions**: ohos.permission.ACCESS_CERT_MANAGER and ohos.permission.ACCESS_CERT_MANAGER_INTERNAL

**System capability**: System SystemCapability.Security.CertificateManager

**System API**: This is a system API.

**Since**: 26.0.0

**Parameters**

| Name      | Type      | Mandatory|Description                                           |
| ------------ | ---------- | ---- |---------------------------------------------------|
| keyUri       | string     | Yes |Unique identifier of a user's public credential.|
| clientAppUid | number        | Yes |Application UID.|

**Return value**

| Type                           | Description                                                        |
| ------------------------------- | ------------------------------------------------------------ |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Certificate Management Error Codes](errorcode-certManager.md).

| ID   | Error Message                                                                                                                                           |
| ----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| 201                    | Permission verification failed. The application does not have the permission required to call the API. |
| 202                    | Permission verification failed. A non-system application calls a system API. |
| 401                    | Parameter verification failed. Possible causes: the URI is null or the URI format is wrong. |
| 17500001               | Internal error. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error. Please try again. |
| 17500002               | Indicates that the certificate does not exist. |

**Example**

```ts
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

let keyUri: string = 'test'; /* Unique identifier of the user public credential. */
let clientAppUid: number = 1001; /* Application UID */
try {
    certificateManager.removeGrantedPublicCertificate(keyUri, clientAppUid).then(() => {
        console.info('Succeeded in removing granted public certificate.');
    }).catch((err: BusinessError) => {
        console.error(`Failed to remove granted public certificate. Code: ${err.code}, message: ${err.message}`);
    })
} catch (error: BusinessError) {
    console.error(`Failed to remove granted public certificate. Code: ${error.code}, message: ${error.message}`);
}
```

## certificateManager.getAllAppPrivateCertificatesByUid

getAllAppPrivateCertificatesByUid(appUid: number) : Promise\<CMResult>

Obtains all private credentials of a specified application. This API is called only by the certificate management application. This API uses a promise to return the result.

**Required permissions**: ohos.permission.ACCESS_CERT_MANAGER and ohos.permission.ACCESS_CERT_MANAGER_INTERNAL

**System capability**: System SystemCapability.Security.CertificateManager

**System API**: This is a system API.

**Since**: 26.0.0

**Parameters**

| Name  | Type                                             | Mandatory| Description                      |
| -------- | ------------------------------------------------- | ---- | -------------------------- |
| appUid | number                   | Yes  | Application UID.|

**Return value**

| Type                           | Description                                                        |
| ------------------------------- | ------------------------------------------------------------ |
| Promise\<[CMResult](js-apis-certManager.md#cmresult)> | Promise used to return the operation result, that is, **credentialDetailList** in the [CMResult](js-apis-certManager.md#cmresult) object.<br>Note: If the number of private credentials is 0, the returned **CMResult** is **undefined**.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Certificate Management Error Codes](errorcode-certManager.md).

| ID   | Error Message                                                                                                                                           |
| ----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| 201                    | Permission verification failed. The application does not have the permission required to call the API. |
| 202                    | Permission verification failed. A non-system application calls a system API. |
| 17500001               | Internal error. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error. Please try again. |

**Example**

```ts
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

let appUid: number = 1001; /* Application UID */
try {
    certificateManager.getAllAppPrivateCertificatesByUid(appUid).then((cmResult: certificateManager.CMResult) => {
        if (cmResult === undefined) { // If the number of private credentials is 0, return undefined in cmResult.
            console.info('The count of private certificates is 0.');
        } else if (cmResult.credentialDetailList == undefined) {
            console.info('The result of getting all private certificates is undefined.');
        } else {
            let list: Array<certificateManager.Credential> = cmResult.credentialDetailList;
            console.info('Succeeded in getting all private certificates.');
        }
    }).catch((err: BusinessError) => {
        console.error(`Failed to get all private certificates. Code: ${err.code}, message: ${err.message}`);
    })
} catch (error: BusinessError) {
    console.error(`Failed to get all private certificates. Code: ${error.code}, message: ${error.message}`);
}
```

## certificateManager.installSystemAppCertificate

installSystemAppCertificate(keystore: Uint8Array, keystorePwd: string): Promise\<CMResult>

Installs the system application credential. This API is called only by the certificate management application. This API uses a promise to return the result.

**Required permissions**: ohos.permission.ACCESS_CERT_MANAGER and ohos.permission.ACCESS_SYSTEM_APP_CERT

**System capability**: System SystemCapability.Security.CertificateManager

**System API**: This is a system API.

**Since**: 26.0.0

**Parameters**

| Name     | Type      | Mandatory|Description                                           |
| ----------- | ---------- | ---- |---------------------------------------------------|
| keystore    | Uint8Array | Yes |Keystore file containing the key pair and certificate. Only the P12 format is supported.|
| keystorePwd | string     | Yes |Password of the keystore file.|

**Return value**

| Type                           | Description                                                        |
| ------------------------------- | ------------------------------------------------------------ |
| Promise\<[CMResult](js-apis-certManager.md#cmresult)> | Promise used to return the operation result, that is, **uri** in the [CMResult](js-apis-certManager.md#cmresult) object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Certificate Management Error Codes](errorcode-certManager.md).

| ID   | Error Message                                                                                                                                           |
| ----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| 201                    | Permission verification failed. The application does not have the permission required to call the API. |
| 202                    | Permission verification failed. A non-system application calls a system API. |
| 401                    | Parameter verification failed. Possible causes: The keystore parameter is empty or exceeds the maximum length. |
| 17500001               | Internal error. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error. Please try again. |
| 17500003               | Indicates that the certificate is in an invalid format. |
| 17500004               | Indicates that the number of certificates reaches the maximum allowed. |
| 17500008               | Indicates that the password is error. |

**Example**

```ts
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

/* The data of the credential to be installed must be assigned based on the service. The data in this example is not the real credential data. */
let keystore: Uint8Array = new Uint8Array([
    0x30, 0x82, 0x0b, 0xc1, 0x02, 0x01,
]);
let keystorePwd: string = "123456";
try {
    certificateManager.installSystemAppCertificate(keystore, keystorePwd).then((cmResult: certificateManager.CMResult) => {
        let uri: string = (cmResult?.uri == undefined) ? '' : cmResult.uri;
        console.info('Succeeded in installing system app certificate.');
    }).catch((err: BusinessError) => {
        console.error(`Failed to install system app certificate. Code: ${err.code}, message: ${err.message}`);
    })
} catch (error: BusinessError) {
    console.error(`Failed to install system app certificate. Code: ${error.code}, message: ${error.message}`);
}
```

## certificateManager.getSystemAppCertificate

getSystemAppCertificate(keyUri: string) : Promise\<CMResult>

Obtains the credential details of the system application. This API is called only by the certificate management application. This API uses a promise to return the result.

**Required permissions**: ohos.permission.ACCESS_CERT_MANAGER and ohos.permission.ACCESS_SYSTEM_APP_CERT

**System capability**: System SystemCapability.Security.CertificateManager

**System API**: This is a system API.

**Since**: 26.0.0

**Parameters**

| Name  | Type                                             | Mandatory| Description                      |
| -------- | ------------------------------------------------- | ---- | -------------------------- |
| keyUri | string                   | Yes  | Unique identifier of a system application credential.|

**Return value**

| Type                           | Description                                                        |
| ------------------------------- | ------------------------------------------------------------ |
| Promise\<[CMResult](js-apis-certManager.md#cmresult)> | Promise used to return the operation result, that is, **credential** in the [CMResult](js-apis-certManager.md#cmresult) object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Certificate Management Error Codes](errorcode-certManager.md).

| ID   | Error Message                                                                                                                                           |
| ----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| 201                    | Permission verification failed. The application does not have the permission required to call the API. |
| 202                    | Permission verification failed. A non-system application calls a system API. |
| 401                    | Parameter verification failed. Possible causes: the URI is null or the URI format is wrong. |
| 17500001               | Internal error. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error. Please try again. |
| 17500002               | Indicates that the certificate does not exist. |

**Example**

```ts
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

let keyUri: string = 'test'; /* Unique identifier of the system application credential. */
try {
    certificateManager.getSystemAppCertificate(keyUri).then((cmResult: certificateManager.CMResult) => {
        if (cmResult?.credential == undefined) {
            console.info('The result of getting system app certificate is undefined.');
        } else {
        let cred: certificateManager.Credential = cmResult.credential;
            console.info('Succeeded in getting system app certificate.');
        }
    }).catch((err: BusinessError) => {
        console.error(`Failed to get system app certificate. Code: ${err.code}, message: ${err.message}`);
    })
} catch (error: BusinessError) {
    console.error(`Failed to get system app certificate. Code: ${error.code}, message: ${error.message}`);
}
```

## certificateManager.uninstallSystemAppCertificate

uninstallSystemAppCertificate(keyUri: string) : Promise\<void>

Uninstalls the credential of the system application. This API is called only by the certificate management application. This API uses a promise to return the result.

**Required permissions**: ohos.permission.ACCESS_CERT_MANAGER and ohos.permission.ACCESS_SYSTEM_APP_CERT

**System capability**: System SystemCapability.Security.CertificateManager

**System API**: This is a system API.

**Since**: 26.0.0

**Parameters**

| Name  | Type                                             | Mandatory| Description                      |
| -------- | ------------------------------------------------- | ---- | -------------------------- |
| keyUri | string                   | Yes  | Unique identifier of a system application credential.|

**Return value**

| Type                           | Description                                                        |
| ------------------------------- | ------------------------------------------------------------ |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Certificate Management Error Codes](errorcode-certManager.md).

| ID   | Error Message                                                                                                                                           |
| ----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| 201                    | Permission verification failed. The application does not have the permission required to call the API. |
| 202                    | Permission verification failed. A non-system application calls a system API. |
| 401                    | Parameter verification failed. Possible causes: the URI is null or the URI format is wrong. |
| 17500001               | Internal error. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error. Please try again. |
| 17500002               | Indicates that the certificate does not exist. |

**Example**

```ts
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

let keyUri: string = 'test'; /* Unique identifier of the system application credential. */
try {
    certificateManager.uninstallSystemAppCertificate(keyUri).then(() => {
        console.info('Succeeded in uninstalling system app certificate.');
    }).catch((err: BusinessError) => {
        console.error(`Failed to uninstall system app certificate. Code: ${err.code}, message: ${err.message}`);
    })
} catch (error: BusinessError) {
    console.error(`Failed to uninstall system app certificate. Code: ${error.code}, message: ${error.message}`);
}
```

## certificateManager.uninstallAllAppCertificate

uninstallAllAppCertificate() : Promise\<void>

Uninstalls all system application credentials and public user credentials. This API is called only by the certificate management application. This API uses a promise to return the result.

**Required permissions**: ohos.permission.ACCESS_CERT_MANAGER, ohos.permission.ACCESS_CERT_MANAGER_INTERNAL, and ohos.permission.ACCESS_SYSTEM_APP_CERT

**System capability**: System SystemCapability.Security.CertificateManager

**System API**: This is a system API.

**Since**: 26.0.0

**Return value**

| Type                           | Description                                                        |
| ------------------------------- | ------------------------------------------------------------ |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Certificate Management Error Codes](errorcode-certManager.md).

| ID   | Error Message                                                                                                                                           |
| ----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| 201                    | Permission verification failed. The application does not have the permission required to call the API. |
| 202                    | Permission verification failed. A non-system application calls a system API. |
| 17500001               | Internal error. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error. Please try again. |

**Example**

```ts
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
    certificateManager.uninstallAllAppCertificate().then(() => {
        console.info('Succeeded in uninstalling all app certificates.');
    }).catch((err: BusinessError) => {
        console.error(`Failed to uninstall all app certificates. Code: ${err.code}, message: ${err.message}`);
    })
} catch (error: BusinessError) {
    console.error(`Failed to uninstall all app certificates. Code: ${error.code}, message: ${error.message}`);
}
```
