# @ohos.security.certManagerDialog (Certificate Management Dialog Box)

<!--Kit: Device Certificate Kit-->
<!--Subsystem: Security-->
<!--Owner: @chaceli-->
<!--Designer: @chande-->
<!--Tester: @zhangzhi1995-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=a16dcd5380f352b729da625973de1c33bd7c6a2a translatedAt=2026-06-10T11:02:57.983Z pushedAt=2026-06-11T11:23:33.679Z -->

The **certManagerDialog** module provides APIs for opening the certificate management pages, on which the certificates are installed, uninstalled, and authorized.

> **NOTE**
>
> The initial APIs of this module are supported since API version 13. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { certificateManagerDialog } from '@kit.DeviceCertificateKit';
```

## CertificateDialogPageType

Enumerates the page types of the certificate management dialog box.

**System capability**: SystemCapability.Security.CertificateManagerDialog

**Model restriction**: This API can be used only in the stage model.

| Name      | Value|  Description     |
| ---------- | ------ | --------- |
| PAGE_MAIN | 1      | Main page of the Certificate Manager application.|
| PAGE_CA_CERTIFICATE | 2      | CA certificate list page.|
| PAGE_CREDENTIAL | 3      | Credential list page.|
| PAGE_INSTALL_CERTIFICATE | 4      | Certificate installation page.|

## CertificateType<sup>14+</sup>

Enumerates the types of the certificate to be installed.

**System capability**: SystemCapability.Security.CertificateManagerDialog

**Model restriction**: This API can be used only in the stage model.

| Name      | Value|  Description     |
| ---------- | ------ | --------- |
| CA_CERT | 1      | CA certificate.|
| CREDENTIAL_USER<sup>22+</sup> | 2      | User public credential.|
| CREDENTIAL_APP<sup>22+</sup> | 3      | Private credential of an application.|
| CREDENTIAL_UKEY<sup>22+</sup> | 4      | USB Key certificate credential. |
| CREDENTIAL_SYSTEM<sup>23+</sup> | 5      | System credential.|

## CertificateScope<sup>14+</sup>

Defines the usage scope of the certificate to be installed.

**System capability**: SystemCapability.Security.CertificateManagerDialog

**Model restriction**: This API can be used only in the stage model.

| Name      | Value|  Description     |
| ---------- | ------ | --------- |
| NOT_SPECIFIED<sup>18+</sup>  | 0      | The usage scope is not specified.|
| CURRENT_USER | 1      | Current user. The certificate is available only to the current login user. |
| GLOBAL_USER<sup>18+</sup> | 2      | All users. The certificate is available to all users. |

## CertificateDialogErrorCode

Enumerates the error codes reported when the certificate management dialog box APIs are called.

**System capability**: SystemCapability.Security.CertificateManagerDialog

**Model restriction**: This API can be used only in the stage model.

| Name      | Value|  Description     |
| ---------- | ------ | --------- |
| ERROR_GENERIC  | 29700001      | An internal error occurs when the API is called, such as IPC failure, memory operation failure, and file operation failure. |
| ERROR_OPERATION_CANCELED<sup>14+</sup>  | 29700002      | The user cancels the operation in the certificate management dialog box. |
| ERROR_OPERATION_FAILED<sup>14+</sup>  | 29700003      | The user operation in the certificate management dialog box fails.<br>For example, the certificate fails to be installed. |
| ERROR_DEVICE_NOT_SUPPORTED<sup>14+</sup>  | 29700004      | This API is not supported on the device. |
| ERROR_NOT_COMPLY_SECURITY_POLICY<sup>18+</sup>  | 29700005      | The operation does not comply with the device security policy.<br>For example, the CA certificate of **GLOBAL_USER** is not allowed on the device. |
| ERROR_PARAMETER_VALIDATION_FAILED<sup>22+</sup>  | 29700006      | The input parameter validation fails.<br>For example, the parameter format is incorrect or the value range is invalid. |
| ERROR_NO_AVAILABLE_CERTIFICATE<sup>22+</sup>  | 29700007      | No certificate is available.|

## CertificateDialogProperty<sup>18+</sup>

Defines the property of the certificate management dialog box.

**System capability**: SystemCapability.Security.CertificateManagerDialog

**Model restriction**: This API can be used only in the stage model.

| Name             | Type   | Read-Only| Optional| Description                        |
| ----------------- | ------- | ---- | ---- | ---------------------------- |
| showInstallButton | boolean | No  | No  | Whether to display the button for installing the certificate. The value **true** means to display the button; the value **false** means the opposite.|

## CertReference<sup>22+</sup>

Represents the reference information of the credential.

**System capability**: SystemCapability.Security.CertificateManagerDialog

**Model restriction**: This API can be used only in the stage model.

| Name             | Type   | Read-Only| Optional| Description                        |
| ----------------- | ------- | ---- | ---- | ---------------------------- |
| certType | [CertificateType](#certificatetype14)   | No  | No  | Certificate type.|
| keyUri | string   | No  | No  | Unique identifier of the credential. The value contains up to 256 bytes.|

## UkeyAuthRequest<sup>22+</sup>

Requests the USB Key PIN authentication.

**System capability**: SystemCapability.Security.CertificateManagerDialog

**Model restriction**: This API can be used only in the stage model.

| Name             | Type   | Read-Only| Optional| Description                        |
| ----------------- | ------- | ---- | ---- | ---------------------------- |
| keyUri | string   | No   | No   | Unique identifier of the USB Key certificate credential. The value contains up to 256 bytes. The value can be obtained using [openAuthorizeDialog](#certificatemanagerdialogopenauthorizedialog22). The result contains **CertReference**. |

## AuthorizeRequest<sup>22+</sup>

Represents the authorization request information of the credential.

**System capability**: SystemCapability.Security.CertificateManagerDialog

**Model restriction**: This API can be used only in the stage model.

| Name             | Type   | Read-Only| Optional| Description                        |
| ----------------- | ------- | ---- | ---- | ---------------------------- |
| certTypes | Array<[CertificateType](#certificatetype14)>   | No  | No  | List of certificate types.|
| certPurpose | [certificateManager.CertificatePurpose](js-apis-certManager.md#certificatepurpose22)    | No   | Yes   | Certificate usage.<br>If the **certTypes** parameter contains the **CertificateType.CREDENTIAL_UKEY** type, the **certPurpose** parameter takes effect, indicating that the USB Key certificate credential is filtered based on the specified certificate usage. |

## certificateManagerDialog.openCertificateManagerDialog

openCertificateManagerDialog(context: common.Context, pageType: CertificateDialogPageType): Promise\<void>

The **certificateManagerDialog** module provides APIs for opening the certificate management pages, on which the certificates are viewed, installed, and uninstalled. This API uses a promise to return the result.

**Required permissions**: ohos.permission.ACCESS_CERT_MANAGER

**System capability**: SystemCapability.Security.CertificateManagerDialog

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name  | Type                                             | Mandatory| Description                      |
| -------- | ------------------------------------------------- | ---- | -------------------------- |
| context | [common.Context](../apis-ability-kit/js-apis-app-ability-common.md#context)                   | Yes   | Context of the application. |
| pageType | [CertificateDialogPageType](#certificatedialogpagetype)                   | Yes  | Type of the page to display.|

**Return value**

| Type                                       | Description                |
| ------------------------------------------- | -------------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Certificate Management Dialog Box Error Codes](errorcode-certManagerDialog.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verification failed. The application does not have the permission required to call the API.     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 29700001 | Internal error. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error. Please try again.    |

**Example**

```ts
import { certificateManagerDialog } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import { UIContext } from '@kit.ArkUI';

/* context is application context information, which is obtained by the caller. The context here is only an example. */
let context: common.Context = new UIContext().getHostContext() as common.Context;
/* pageType specifies the type of the page to display. In this example, pageType is PAGE_MAIN, which indicates the main page of the Certificate Management application. */
let pageType: certificateManagerDialog.CertificateDialogPageType = certificateManagerDialog.CertificateDialogPageType.PAGE_MAIN;
try {
  certificateManagerDialog.openCertificateManagerDialog(context, pageType).then(() => {
    console.info('Succeeded in opening certificate manager dialog.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to open certificate manager dialog. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error) {
  console.error(`Failed to open certificate manager dialog. Code: ${error.code}, message: ${error.message}`);
}
```

## certificateManagerDialog.openInstallCertificateDialog<sup>14+</sup>

openInstallCertificateDialog(context: common.Context, certType: CertificateType, certScope: CertificateScope, cert: Uint8Array): Promise\<string>

Opens a dialog box for installing a certificate. After the certificate is installed, the unique identifier of the certificate is returned. The application can use the certificate based on the identifier. This API uses a promise to return the result.

**Required permissions**: ohos.permission.ACCESS_CERT_MANAGER

**System capability**: SystemCapability.Security.CertificateManagerDialog

**Device behavior differences**: This API can be properly called on PCs and 2-in-1 devices. If this API is called on other device types and **certType** is set to **CA_CERT**, error code 29700004 is returned.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name  | Type                                             | Mandatory| Description                      |
| -------- | ------------------------------------------------- | ---- | -------------------------- |
| context | [common.Context](../apis-ability-kit/js-apis-app-ability-common.md#context) | Yes | Context of the application. |
| certType | [CertificateType](#certificatetype14) | Yes | Type of the certificate to install. Only **CA_CERT**, **CREDENTIAL_USER**, and **CREDENTIAL_SYSTEM** are currently supported. |
| certScope | [CertificateScope](#certificatescope14) | Yes | Usage scope of the certificate to install. Only **CURRENT_USER** and **NOT_SPECIFIED** are currently supported. |
| cert | Uint8Array                  | Yes  | Data of the certificate to install.|

**Return value**

| Type                                       | Description                |
| ------------------------------------------- | -------------------- |
| Promise\<string> | Promise used to return the certificate URI. The value contains up to 256 bytes.|

**Error codes**

For details about the error codes, see [Certificate Management Dialog Box Error Codes](errorcode-certManagerDialog.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verification failed. The application does not have the permission required to call the API.     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 29700001 | Internal error. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error. Please try again.     |
| 29700002 | The user cancels the installation operation.     |
| 29700003 | The user install certificate failed in the certificate manager dialog, such as the certificate is in an invalid format.     |
| 29700004 | The API is not supported on this device.     |
| 29700005 | The operation does not comply with the device security policy, such as the device does not allow users to manage the ca certificate of the global user.     |

**Example**

```ts
import { certificateManagerDialog } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import { UIContext } from '@kit.ArkUI';

/* context is application context information, which is obtained by the caller. The context here is only an example. */
let context: common.Context = new UIContext().getHostContext() as common.Context;
/* certificateType specifies the certificate type. The value CA_CERT here indicates a CA certificate. */
let certificateType: certificateManagerDialog.CertificateType = certificateManagerDialog.CertificateType.CA_CERT;
/* certificateScope specifies the usage scope of the certificate. The value CURRENT_USER here means the certificate can be used by the current user. */
let certificateScope: certificateManagerDialog.CertificateScope = certificateManagerDialog.CertificateScope.CURRENT_USER;
/* The CA certificate data must be assigned by the service. In this example, the data is not CA certificate data. */
let caCert: Uint8Array = new Uint8Array([
  0x30, 0x82, 0x0b, 0xc1, 0x02, 0x01,
]);
try {
  certificateManagerDialog.openInstallCertificateDialog(context, certificateType, certificateScope, caCert).then((uri: string) => {
    console.info('Succeeded in opening install certificate');
  }).catch((err: BusinessError) => {
    console.error(`Failed to open install certificate dialog. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error) {
  console.error(`Failed to open install certificate dialog. Code: ${error.code}, message: ${error.message}`);
}
```

## certificateManagerDialog.openUninstallCertificateDialog<sup>18+</sup>

openUninstallCertificateDialog(context: common.Context, certType: CertificateType, certUri: string): Promise\<void>

Opens a dialog box for uninstalling a certificate. This API uses a promise to return the result.

**Required permissions**: ohos.permission.ACCESS_CERT_MANAGER

**System capability**: SystemCapability.Security.CertificateManagerDialog

**Device support**: This API is available on PCs/2-in-1 devices. For other devices, error code 29700004 is returned.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name  | Type                                             | Mandatory| Description                      |
| -------- | ------------------------------------------------- | ---- | -------------------------- |
| context | [common.Context](../apis-ability-kit/js-apis-app-ability-common.md#context)                   | Yes   | Context of the application. |
| certType | [CertificateType](#certificatetype14)                   | Yes   | Type of the certificate to uninstall. Only **CA_CERT** is currently supported. |
| certUri | string                  | Yes   | Unique identifier of the certificate to uninstall. The value contains up to 256 bytes. |

**Return value**

| Type                                       | Description                |
| ------------------------------------------- | -------------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Certificate Management Dialog Box Error Codes](errorcode-certManagerDialog.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verification failed. The application does not have the permission required to call the API.     |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 29700001 | Internal error. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error. Please try again.     |
| 29700002 | The user cancels the uninstallation operation.     |
| 29700003 | The user uninstall certificate failed in the certificate manager dialog, such as the certificate uri is not exist.     |
| 29700004 | The API is not supported on this device.     |
| 29700005 | The operation does not comply with the device security policy, such as the device does not allow users to manage the ca certificate of the global user.     |

**Example**

```ts
import { certificateManagerDialog } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import { UIContext } from '@kit.ArkUI';

/* context is application context information, which is obtained by the caller. The context here is only an example. */
let context: common.Context = new UIContext().getHostContext() as common.Context;
/* certificateType specifies the certificate type. The value CA_CERT indicates a CA certificate is deleted. */
let certificateType: certificateManagerDialog.CertificateType = certificateManagerDialog.CertificateType.CA_CERT;
/* certUri is the unique identifier of the certificate installed. The value here is only an example. */
let certUri: string = "test";
try {
  certificateManagerDialog.openUninstallCertificateDialog(context, certificateType, certUri).then(() => {
    console.info('Succeeded in opening uninstall certificate');
  }).catch((err: BusinessError) => {
    console.error(`Failed to open uninstall certificate dialog. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error) {
  console.error(`Failed to open uninstall certificate dialog. Code: ${error.code}, message: ${error.message}`);
}
```

## certificateManagerDialog.openCertificateDetailDialog<sup>18+</sup>

openCertificateDetailDialog(context: common.Context, cert: Uint8Array, property: CertificateDialogProperty): Promise\<void>

Opens the certificate management dialog box and displays the certificate details, such as the basic information, validity period, issuer, and user of the certificate. This API uses a promise to return the result.

**Required permissions**: ohos.permission.ACCESS_CERT_MANAGER

**System capability**: SystemCapability.Security.CertificateManagerDialog

**Device support**: This API is available on PCs/2-in-1 devices. For other devices, error code 29700004 is returned.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name  | Type                                             | Mandatory| Description                      |
| -------- | ------------------------------------------------- | ---- | -------------------------- |
| context | [common.Context](../apis-ability-kit/js-apis-app-ability-common.md#context)                   | Yes   | Context of the application. |
| cert     | Uint8Array                                                   | Yes  | Data of the certificate to install.            |
| property | [CertificateDialogProperty](#certificatedialogproperty18) | Yes   | Property of the certificate management dialog box. |

**Return value**

| Type                                       | Description                |
| ------------------------------------------- | -------------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Certificate Management Dialog Box Error Codes](errorcode-certManagerDialog.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 29700001 | Internal error. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error. Please try again.                |
| 29700003 | Show the certificate detail dialog failed, such as the certificate is in an invalid format. |
| 29700004 | The API is not supported on this device.                     |

**Example**

```ts
import { certificateManagerDialog } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import { UIContext } from '@kit.ArkUI';

/* context is application context information, which is obtained by the caller. The context here is only an example. */
let context: common.Context = new UIContext().getHostContext() as common.Context;
/* The CA certificate data must be assigned by the service. In this example, the data is not CA certificate data. */
let caCert: Uint8Array = new Uint8Array([
  0x30, 0x82, 0x0b, 0xc1, 0x02, 0x01,
]);
let property: certificateManagerDialog.CertificateDialogProperty = {
  showInstallButton: false /* Do not display the button for installing the certificate.*/
};
try {
  certificateManagerDialog.openCertificateDetailDialog(context, caCert, property).then(() => {
    console.info('Succeeded in opening certificate detail dialog.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to open certificate detail dialog. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error) {
  console.error(`Failed to open certificate detail dialog. Code: ${error.code}, message: ${error.message}`);
}
```

## certificateManagerDialog.openAuthorizeDialog<sup>20+</sup>

openAuthorizeDialog(context: common.Context): Promise\<string>

Opens the certificate credential authorization page of the certificate management dialog box to grant a certificate credential to the application. After the API is successfully called, the application can perform signing, signature verification, and details query based on the URI of the authorized certificate credential returned by the API. This API uses a promise to return the result.

**Required permissions**: ohos.permission.ACCESS_CERT_MANAGER

**System capability**: SystemCapability.Security.CertificateManagerDialog

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name    | Type                                                                | Mandatory| Description         |
|---------|--------------------------------------------------------------------|----|-------------|
| context | [common.Context](../apis-ability-kit/js-apis-app-ability-common.md#context) | Yes | Context of the application. |

**Return value**

| Type              | Description                                  |
|------------------|--------------------------------------|
| Promise\<string> | Promise used to return the URI of the certificate authorized. The value contains up to 256 bytes.|

**Error codes**

For details about the error codes, see [Certificate Management Dialog Box Error Codes](errorcode-certManagerDialog.md).

| Error Code   | Error Message                                                                                                                                           |
|----------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| 201      | Permission verification failed. The application does not have the permission required to call the API.                                          |
| 401      | Invalid parameter. Possible causes: 1. A mandatory parameter is left unspecified. 2. Incorrect parameter type. 3. Parameter verification failed. |
| 29700001 | Internal error. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error. Please try again.        |
| 29700002 | The user cancels the authorization.                                                                                                             |

**Example**

```ts
import { certificateManagerDialog } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import { UIContext } from '@kit.ArkUI';

/* context is application context information, which is obtained by the caller. The context here is only an example. */
let context: common.Context = new UIContext().getHostContext() as common.Context;
try {
    certificateManagerDialog.openAuthorizeDialog(context).then((uri: string) => {
        console.info(`Succeeded in authorizing certificate, uri: ${uri}`)
    }).catch((err: BusinessError) => {
        console.error(`Failed to authorize certificate. Code: ${err.code}, message: ${err.message}`);
    });
} catch (err) {
    let error = err as BusinessError;
    console.error(`Failed to authorize certificate. Code: ${error.code}, message: ${error.message}`);
}
```

## certificateManagerDialog.openAuthorizeDialog<sup>22+</sup>

openAuthorizeDialog(context: common.Context, authorizeRequest: AuthorizeRequest): Promise\<CertReference>

Opens the certificate credential authorization page of the certificate management dialog box to grant a certificate credential to the application. After the API is successfully called, the application can perform signing, signature verification, and details query based on the URI of the authorized certificate credential returned by the API. The certificate types that can be authorized include the application certificate credential, user certificate credential, and USB Key certificate credential. This API uses a promise to return the result.

**Required permissions**: ohos.permission.ACCESS_CERT_MANAGER

**System capability**: SystemCapability.Security.CertificateManagerDialog

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name    | Type                                                                | Mandatory| Description         |
|---------|--------------------------------------------------------------------|----|-------------|
| context | [common.Context](../apis-ability-kit/js-apis-app-ability-common.md#context) | Yes  | Context of the application. |
| authorizeRequest | [AuthorizeRequest](#authorizerequest22) | Yes | Authorization request information.|

**Return value**

| Type              | Description                                  |
|------------------|--------------------------------------|
| Promise\<[CertReference](#certreference22)> | Promise used to return the result of the authorization certificate reference.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Certificate Management Dialog Box Error Codes](errorcode-certManagerDialog.md).

| Error Code   | Error Message                                                                                                                                           |
|----------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| 201      | Permission verification failed. The application does not have the permission required to call the API.                                          |
| 801      | Capability not supported.  |
| 29700001 | Internal error. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error; 4. Call other service failed. Please try again.                 |
| 29700002 | The user cancels the authorization.                                                                                                             |
| 29700006 | Indicates that the input parameters validation failed. for example, the parameter format is incorrect or the value range is invalid.            |
| 29700007 | No available certificate for authorization. Possible causes: 1. No certificate matches the filter criteria; 2. All certificates have been deleted.            |

**Example**

```ts
import { certificateManagerDialog, certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import { UIContext } from '@kit.ArkUI';

/* context is application context information, which is obtained by the caller. The context here is only an example. */
let context: common.Context = new UIContext().getHostContext() as common.Context;
let certTypes: Array<certificateManagerDialog.CertificateType> = [
  certificateManagerDialog.CertificateType.CREDENTIAL_USER,
  certificateManagerDialog.CertificateType.CREDENTIAL_APP,
  certificateManagerDialog.CertificateType.CREDENTIAL_UKEY
];
let certPurpose: certificateManager.CertificatePurpose = certificateManager.CertificatePurpose.PURPOSE_DEFAULT;
let authorizeRequest: certificateManagerDialog.AuthorizeRequest = { certTypes: certTypes, certPurpose: certPurpose };
try {
    certificateManagerDialog.openAuthorizeDialog(context, authorizeRequest).then((certReference: certificateManagerDialog.CertReference) => {
      let reference = certReference;
      console.info(`Succeeded in opening authorize dialog.`)
    }).catch((err: BusinessError) => {
        console.error(`Failed to open authorize dialog. Code: ${err.code}, message: ${err.message}`);
    });
} catch (err) {
    let error = err as BusinessError;
    console.error(`Failed to open authorize dialog. Code: ${error.code}, message: ${error.message}`);
}
```

## certificateManagerDialog.openUkeyAuthDialog<sup>22+</sup>

openUkeyAuthDialog(context: common.Context, ukeyAuthRequest: UkeyAuthRequest): Promise\<void>

Opens the PIN credential authentication page of the USB Key certificate management dialog box. On the displayed page, the user can enter the PIN to authorize the USB Key certificate credential. After the API is successfully called, the USB Key certificate credential is unlocked, and the application can use the credential for operations such as signing and encryption. This API uses a promise to return the result.

**Required permissions**: ohos.permission.ACCESS_CERT_MANAGER

**System capability**: SystemCapability.Security.CertificateManagerDialog

**Device behavior differences**: This API can be properly called on PCs. If it is called on other device types, error code 801 is returned.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name    | Type                                                                | Mandatory| Description         |
|---------|--------------------------------------------------------------------|----|-------------|
| context | [common.Context](../apis-ability-kit/js-apis-app-ability-common.md#context) | Yes | Context of the application. |
| ukeyAuthRequest | [UkeyAuthRequest](#ukeyauthrequest22) | Yes | Authorization request information of the USB Key certificate credential. |

**Return value**

| Type              | Description                                  |
|------------------|--------------------------------------|
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Certificate Management Dialog Box Error Codes](errorcode-certManagerDialog.md).

| Error Code   | Error Message                                                                                                                                           |
|----------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| 201      | Permission verification failed. The application does not have the permission required to call the API.                                          |
| 801      | Capability not supported.  |
| 29700001 | Internal error. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error. Please try again.           |
| 29700002 | The user cancels the authentication operation.                                                                                                             |
| 29700003 | The authentication operation failed, such as the USB key certificate does not exist, the USB key status is abnormal.                              |
| 29700006 | Indicates that the input parameters validation failed. For example, the parameter format is incorrect or the value range is invalid.            |

**Example**

```ts
import { certificateManagerDialog } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import { UIContext } from '@kit.ArkUI';

/* context is application context information, which is obtained by the caller. The context here is only an example. */
let context: common.Context = new UIContext().getHostContext() as common.Context;
/* keyUri is the unique identifier of the credential. The invoker obtains the value by itself. The value here is only an example. */
let keyUri: string = "test"
let ukeyAuthRequest: certificateManagerDialog.UkeyAuthRequest = { keyUri: keyUri }
try {
    certificateManagerDialog.openUkeyAuthDialog(context, ukeyAuthRequest).then(() => {
        console.info(`Succeeded in opening ukey authorization dialog`)
    }).catch((err: BusinessError) => {
        console.error(`Failed to open ukey authorization dialog. Code: ${err.code}, message: ${err.message}`);
    });
} catch (err) {
    let error = err as BusinessError;
    console.error(`Failed to open ukey authorization dialog. Code: ${error.code}, message: ${error.message}`);
}
```