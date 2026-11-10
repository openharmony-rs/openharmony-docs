# @ohos.enterprise.securityManager (Security Management)
<!--Kit: MDM Kit-->
<!--Subsystem: Customization-->
<!--Owner: @huanleima; @weizai16-->
<!--Designer: @hp_guo-->
<!--Tester: @lpw_work-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=06427ce882491fa79e50e9e08245cbbbe238a7a3 translatedAt=2026-11-03T05:26:33.037Z pushedAt=2026-11-03T12:08:25.559Z nl=1 -->

This module provides enterprise device security management capabilities, including certificate management, device security policy management, password policy management, clipboard policy management, watermark policy management, and permission management. Enterprises can use this module to monitor the device security status in real time, manage the lifecycle of enterprise certificates, configure device password policies in a unified manner, control the use of the app clipboard, set screen and app watermarks to prevent information leakage, and implement refined management of app permissions. This helps enterprises enhance device security protection capabilities and reduce data leakage risks.

> **NOTE**
>
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.
>
> The APIs of this module can be called only by a device administrator application that is enabled. For details, see [MDM Kit Development](../../mdm/mdm-kit-guide.md).

## Modules to Import

```ts
import { securityManager } from '@kit.MDMKit';
```

## securityManager.uninstallUserCertificate

uninstallUserCertificate(admin: Want, certUri: string): Promise&lt;void&gt;

Uninstalls a user certificate. This API uses a promise to return the result. This API is applicable to enterprise certificate management scenarios, such as replacing an expired certificate and revoking an employee's access to enterprise resources. Enterprises can call this API to uninstall a certificate when the certificate expires, is replaced, or is no longer needed, ensuring the flexibility and security of device certificate management.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_CERTIFICATE

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name | Type                                                   | Mandatory| Description                             |
| ------- | ------------------------------------------------------- | ---- | --------------------------------- |
| admin   | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.                   |
| certUri | string                                                  | Yes  | Certificate URI, which is set and returned by the [installUserCertificate](#securitymanagerinstallusercertificate) API for installing a user certificate.|

**Return value**

| Type               | Description                                                        |
| ------------------- | ------------------------------------------------------------ |
| Promise&lt;void&gt; | Promise that returns no value. An error object is thrown when a user certificate fails to be uninstalled.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9201001  | Failed to manage the certificate.                            |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { securityManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace with actual values.
let aliasStr = "certName";
securityManager.uninstallUserCertificate(wantTemp, aliasStr).then(() => {
  console.info(`Succeeded in uninstalling user certificate.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to uninstall user certificate. Code is ${err.code}, message is ${err.message}`);
});
```

## securityManager.installUserCertificate

installUserCertificate(admin: Want, certificate: CertBlob): Promise&lt;string&gt;

Installs a user certificate. This API uses a promise to return the result. Enterprises can use this API to install certificates on devices in scenarios such as enterprise VPN connection, security authentication, and digital signatures, implementing enterprise-level secure communication and data protection.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_CERTIFICATE

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name     | Type                                                   | Mandatory| Description          |
| ----------- | ------------------------------------------------------- | ---- | -------------- |
| admin       | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|
| certificate | [CertBlob](#certblob)                                   | Yes  | Certificate information. The certificate file must be stored in the path that the app has the permission to access, such as the app sandbox path. For details about the mapping between the app sandbox path and the actual physical path, see [Mappings Between App Sandbox Paths and Physical Paths](../../file-management/app-sandbox-directory.md#mappings-between-application-sandbox-paths-and-physical-paths).    |

**Return value**

| Type                 | Description                                                |
| --------------------- | ---------------------------------------------------- |
| Promise&lt;string&gt; | Promise used to return the URI of the installed certificate. This URI can be used to uninstall the certificate.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9201001  | Failed to manage the certificate.                            |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

<!--code_no_check-->
```ts
import { securityManager } from '@kit.MDMKit';
import { common, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
let certFileArray: Uint8Array = new Uint8Array();
// Initialize the context variable in the onCreate callback function of the MainAbility.
// Store test.cer in the rawfile directory.
// Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
const context = this.getUIContext().getHostContext() as common.UIAbilityContext;
context.resourceManager.getRawFileContent("test.cer").then((value) => {
  certFileArray = value;
  securityManager.installUserCertificate(wantTemp, { inData: certFileArray, alias: "cert_alias_xts" })
    .then((result) => {
      console.info(`Succeeded in installing user certificate, result : ${JSON.stringify(result)}`);
    }).catch((err: BusinessError) => {
      console.error(`Failed to install user certificate. Code: ${err.code}, message: ${err.message}`);
  });
}).catch((err: BusinessError) => {
  console.error(`Failed to get raw file content. message: ${err.message}`);
  return;
});
```

## securityManager.installUserCertificate<sup>18+</sup>

installUserCertificate(admin: Want, certificate: CertBlob, accountId: number): string

Installs a user certificate based on the system account. Enterprises can install independent certificates for different user accounts, enabling security isolation and personalized certificate management in multi-user environments, thus meeting the security control requirements of multi-user devices.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_CERTIFICATE

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name     | Type                                                   | Mandatory| Description          |
| ----------- | ------------------------------------------------------- | ---- | -------------- |
| admin       | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|
| certificate | [CertBlob](#certblob)                                   | Yes  | Certificate information. The certificate file must be stored in the path that the app has the permission to access, such as the app sandbox path. For details about the mapping between the app sandbox path and the actual physical path, see [Mappings Between App Sandbox Paths and Physical Paths](../../file-management/app-sandbox-directory.md#mappings-between-application-sandbox-paths-and-physical-paths).    |
| accountId   | number                                                  | Yes  | User ID, which must be greater than or equal to 0. You can call [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1) of **@ohos.account.osAccount** to obtain the user ID.|

**Return value**

| Type                 | Description                                                |
| --------------------- | ---------------------------------------------------- |
| string      | URI of the installed certificate, which is used to uninstall the certificate.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9201001  | Failed to manage the certificate.                            |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

<!--code_no_check-->
```ts
import { securityManager } from '@kit.MDMKit';
import { common, Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
let certFileArray: Uint8Array = new Uint8Array();
let accountId: number = 100;
// Initialize the context variable in the onCreate callback function of the MainAbility.
// Store test.cer in the rawfile directory.
// Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
const context = this.getUIContext().getHostContext() as common.UIAbilityContext;
context.resourceManager.getRawFileContent("test.cer").then((value) => {
  certFileArray = value;
  try {
    let result: string = securityManager.installUserCertificate(wantTemp, { inData: certFileArray, alias: "cert_alias_xts" }, accountId);
    console.info(`Succeeded in installing user certificate. result: ${result}`);
  } catch (err) {
    console.error(`Failed to install user certificate. Code: ${err.code}, message: ${err.message}`);
  }
});
```
## securityManager.getUserCertificates<sup>18+</sup>

getUserCertificates(admin: Want, accountId: number): Array&lt;string&gt;

Obtains the user certificate of a specified system account. Enterprises can use this API to query the list of user certificates installed on a device for scenarios such as certificate audit and certificate validity period management, ensuring traceability of certificate management.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_CERTIFICATE

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type                                                   | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin  | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.                                              |
| accountId | number                                               | Yes  | User ID, which must be greater than or equal to 0. You can call [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1) of **@ohos.account.osAccount** to obtain the user ID.|

**Return value**

| Type  | Description                |
| ------ | -------------------- |
| Array&lt;string&gt; | All user certificates installed under the specified user ID.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { securityManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace with actual values.
let accountId: number = 100;
try {
  let result: Array<string> = securityManager.getUserCertificates(wantTemp, accountId);
  console.info(`Succeeded in getting the uri list of user Certificates. result: ${JSON.stringify(result)}`);
} catch (err) {
  console.error(`Failed to get the uri list of user Certificates. Code: ${err.code}, message: ${err.message}`);
}
```

## securityManager.getSecurityStatus

getSecurityStatus(admin: Want, item: string): string

Obtains the security status of the current device. This API is applicable to scenarios such as device compliance check, security status audit, and policy execution effect verification, helping enterprise administrators determine whether devices meet security requirements. Enterprises can use this API to monitor the security patch status and file encryption status of devices in real time, enabling timely detection of device security risks and prompt action to protect enterprise devices and data.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SECURITY

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type                                                   | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin  | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.                                              |
| item   | string                                                  | Yes  | Type of the security status to obtain.<br>- **patch**: device security patch.<br>- **encryption**: device file system encryption.<!--RP1--><!--RP1End-->|

**Return value**

| Type  | Description                |
| ------ | -------------------- |
| string | Security status obtained.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { securityManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  let result: string = securityManager.getSecurityStatus(wantTemp, 'patch');
  console.info(`Succeeded in getting security patch tag. tag: ${result}`);
} catch (err) {
  console.error(`Failed to get security patch tag. Code: ${err.code}, message: ${err.message}`);
}
```

## securityManager.setPasswordPolicy

setPasswordPolicy(admin: Want, policy: PasswordPolicy): void

Sets the device screen lock password policy. After the policy is set, when a user sets a lock screen password, if the password does not meet the requirements, a security prompt will be displayed asking the user to reset the password. This policy is applicable to enterprise security compliance scenarios, such as requiring employees to use strong passwords and change passwords periodically, to reduce the risk of enterprise data leakage.

> **NOTE**
>
> In multiple MDM application scenarios, following the [configuration](../../mdm/mdm-kit-multi-mdm.md#rule-3-latest-configuration-precedence) rule, when any MDM application is deactivated, the device screen lock password policy set by that application will be cleared.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SECURITY

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name     | Type                                      | Mandatory  | Description                      |
| -------- | ---------------------------------------- | ---- | ------------------------------- |
| admin    | [Want](../apis-ability-kit/js-apis-app-ability-want.md)     | Yes   | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.                 |
| policy | [PasswordPolicy](#passwordpolicy) | Yes| Device screen lock password policy.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                                      |
| ------- | ---------------------------------------------------------------------------- |
| 9200001 | The application is not an administrator application of the device.                        |
| 9200002 | The administrator application does not have permission to manage the device. |
| 9200007 | The system ability works abnormally. |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { securityManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

let policy: securityManager.PasswordPolicy = {
  complexityRegex: '^(?=.*[a-z])(?=.*[A-Z])(?=.*\\d)(?=.*[!@#$%^&*])[a-zA-Z\\d!@#$%^&*]{8,}$',
  validityPeriod: 1,
  additionalDescription: 'The password must contain at least eight characters, including at least one uppercase letter, one lowercase letter, one digit, and one special character.',
  passwordAlgs: securityManager.PasswordAlgs.SCRYPT_HKDF_SM4
};
try {
  securityManager.setPasswordPolicy(wantTemp, policy);
  console.info(`Succeeded in setting password policy.`);
} catch (err) {
  console.error(`Failed to set password policy. Code: ${err.code}, message: ${err.message}`);
}
```

## securityManager.getPasswordPolicy

getPasswordPolicy(admin: Want): PasswordPolicy

Obtains the device screen lock password policy. Enterprises can use this API to query the current password policy for policy audit and compliance check, ensuring that the device password policy complies with enterprise security specifications.

This API queries the policy set by the corresponding enterprise device management application by passing in a Want. To query the policy that actually takes effect, use the [securityManager.getPasswordPolicy](#securitymanagergetpasswordpolicy-1) API.

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name     | Type                                      | Mandatory  | Description                      |
| -------- | ---------------------------------------- | ---- | ------------------------------- |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes   | Enterprise device management extension component. The Want must include the abilityName of the enterprise device management extension capability and the bundleName of the application.|

**Return value**

| Type                  | Description                     |
| --------------------- | ------------------------- |
| [PasswordPolicy](#passwordpolicy) | Device screen lock password policy. |

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Information                                                                       |
| ------- | ---------------------------------------------------------------------------- |
| 9200001 | The application is not an administrator application of the device.                        |
| 9200002 | The administrator application does not have permission to manage the device. |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { securityManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace it based on the actual situation.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  let result: securityManager.PasswordPolicy = securityManager.getPasswordPolicy(wantTemp);
  console.info(`Succeeded in getting password policy, result : ${JSON.stringify(result)}`);
} catch (err) {
  console.error(`Failed to get password policy. Code: ${err.code}, message: ${err.message}`);
}
```


## securityManager.getPasswordPolicy

getPasswordPolicy(admin: Want | null): PasswordPolicy

Obtains the device screen lock password policy. Enterprises can use this API to query the current password policy for policy audit and compliance check, ensuring that the device password policy complies with enterprise security specifications.

**Since:** 26.0.0

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SECURITY

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name     | Type                                      | Mandatory  | Description                      |
| -------- | ---------------------------------------- | ---- | ------------------------------- |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) \| null | Yes   | Enterprise device management extension component. The Want must include the abilityName of the enterprise device management extension capability and the bundleName of the application where it resides.<br>When multiple MDM applications exist on the device, passing Want queries the policy set by the corresponding enterprise device management application, while passing null queries the policy that actually takes effect. |

**Return value**

| Type                  | Description                     |
| --------------------- | ------------------------- |
| [PasswordPolicy](#passwordpolicy) | Device screen lock password policy.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                                      |
| ------- | ---------------------------------------------------------------------------- |
| 9200001 | The application is not an administrator application of the device.                        |
| 9200002 | The administrator application does not have permission to manage the device. |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { securityManager } from '@kit.MDMKit';

try {
  // Replace the parameters based on the actual situation.
  let result: securityManager.PasswordPolicy = securityManager.getPasswordPolicy(null);
  console.info(`Succeeded in getting password policy, result : ${JSON.stringify(result)}`);
} catch (err) {
  console.error(`Failed to get password policy. Code: ${err.code}, message: ${err.message}`);
}
```
## securityManager.setScreenLockDisabledForAccount

setScreenLockDisabledForAccount(admin: Want, disable: boolean): void

Disables or enables swipe-to-unlock for the current user. When enabled, the user must swipe on the screen after the screen is turned on to access the home screen. When disabled, the screen goes directly to the home screen after being turned on. This API is suitable for enterprise device management scenarios, such as disabling swipe-to-unlock in specific security environments to simplify operations, or enabling it in general scenarios as a basic security measure.

> **NOTE**
>
> 1. This API takes effect only when no lock screen password is set on the device.
> 
> 2. By default, swipe-to-unlock is enabled on the device.
>
> 3. If a lock screen password exists on the device, disabling swipe-to-unlock fails and error code 9201021 is thrown.
>
> 4. After the policy of disabling swipe-to-unlock is delivered, if the user enters a device password, the password takes effect. The device then requires password verification before entering the home screen, and the previously delivered policy becomes invalid.
>
> 5. In a multi-MDM application scenario, follow the [configuration](../../mdm/mdm-kit-multi-mdm.md#rule-3-latest-configuration-precedence) rule.

**Since:** 26.0.0

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SECURITY

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Device behavior differences**: This API is supported on phones and tablets. On other device types, it returns error code 801.

**Parameters**

| Name | Type                                                   | Mandatory| Description                             |
| ------- | ------------------------------------------------------- | ---- | --------------------------------- |
| admin   | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.                   |
| disable | boolean                                                  | Yes  | Whether to disable swipe-to-unlock for the current user. The value **true** indicates yes, and the value **false** indicates no.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9201021  | A lock screen password has been set for the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**Example**

```ts
import { securityManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
try {
  securityManager.setScreenLockDisabledForAccount(wantTemp, true);
  console.info(`Succeeded in setting screen lock disabled for account.`);
} catch (err) {
  console.error(`Failed to set screen lock disabled for account. Code: ${err.code}, message: ${err.message}`);
}
```

## securityManager.isScreenLockDisabledForAccount

isScreenLockDisabledForAccount(admin: Want): boolean

Checks whether swipe-to-unlock is disabled for the current user.

**Since:** 26.0.0

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SECURITY

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Device behavior differences**: This API is supported on phones and tablets. On other device types, it returns error code 801.

**Parameters**

| Name| Type                                                   | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin  | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.                                              |

**Return value**

| Type   | Description                |
| ------- | -------------------- |
| boolean | The value **true** indicates that swipe-to-unlock is disabled for the current user, and **false** indicates that it is enabled.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**Example**

```ts
import { securityManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
try {
  let result: boolean = securityManager.isScreenLockDisabledForAccount(wantTemp);
  console.info(`Succeeded in checking screen lock disabled for account, result : ${result}`);
} catch (err) {
  console.error(`Failed to check screen lock disabled for account. Code: ${err.code}, message: ${err.message}`);
}
```

## securityManager.setAppClipboardPolicy

setAppClipboardPolicy(admin: Want, tokenId: number, policy: ClipboardPolicy): void

Sets the device clipboard policy. After the policy is set, applications will be restricted in their clipboard usage according to the configured policy. This API is applicable to enterprise data leakage prevention scenarios, such as restricting clipboard usage for sensitive applications (such as enterprise email and financial systems) to prevent sensitive data from being copied to unauthorized applications, thereby reducing the risk of data leakage. Enterprises can use this API to control application clipboard usage permissions, preventing sensitive data from being leaked to unauthorized applications via the clipboard, and enhancing enterprise data security protection capabilities.

> **NOTE**
>
> In a multi-MDM application scenario, follow the [security-first](../../mdm/mdm-kit-multi-mdm.md#rule-1-security-first) rule.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SECURITY

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name     | Type                                      | Mandatory  | Description                      |
| -------- | ---------------------------------------- | ---- | ------------------------------- |
| admin    | [Want](../apis-ability-kit/js-apis-app-ability-want.md)     | Yes   | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.                 |
| tokenId | number | Yes| Application token ID, which can be obtained using [bundleManager.getApplicationInfo](../apis-ability-kit/js-apis-bundleManager-applicationInfo.md).|
| policy | [ClipboardPolicy](#clipboardpolicy) | Yes| Clipboard policy to set.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                                      |
| ------- | ---------------------------------------------------------------------------- |
| 9200001 | The application is not an administrator application of the device.                        |
| 9200002 | The administrator application does not have permission to manage the device. |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { securityManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace with actual values.
let tokenId: number = 586874394;
try {
  securityManager.setAppClipboardPolicy(wantTemp, tokenId, securityManager.ClipboardPolicy.IN_APP);
  console.info(`Succeeded in setting clipboard policy.`);
} catch (err) {
  console.error(`Failed to set clipboard policy. Code: ${err.code}, message: ${err.message}`);
}
```

## securityManager.getAppClipboardPolicy

getAppClipboardPolicy(admin: Want, tokenId?: number): string

Obtains the device clipboard policy. Enterprises can use this API to query the currently configured clipboard policy for policy auditing and compliance checks, ensuring that the clipboard control policy meets enterprise security requirements.

This API queries the policy set by the corresponding enterprise device management application by passing in a Want. To query the policy that actually takes effect, use the [securityManager.getAppClipboardPolicy](#securitymanagergetappclipboardpolicy-1) API.

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name    | Type                                                     | Mandatory | Description                                                                                                          
| -------- | ---------------------------------------- | ---- | ------------------------------- |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes   | Enterprise device management extension component. The Want must include the abilityName of the enterprise device management extension capability and the bundleName of the application.|
| tokenId | number | No | Identity of the target application. You can obtain the accessTokenId through [bundleManager.getApplicationInfo](../apis-ability-kit/js-apis-bundleManager-applicationInfo.md). |

**Return value:**

| Type                   | Description                      |
| --------------------- | ------------------------- |
| string | JSON string of the device clipboard policy.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                                       |
| ------- | ---------------------------------------------------------------------------- |
| 9200001 | The application is not an administrator application of the device.                        |
| 9200002 | The administrator application does not have permission to manage the device. |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { securityManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace it based on the actual situation.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace it based on the actual situation.
let tokenId: number = 586874394;
try {
  let result: string = securityManager.getAppClipboardPolicy(wantTemp, tokenId);
  console.info(`Succeeded in getting clipboard policy, result : ${result}`);
} catch (err) {
  console.error(`Failed to get clipboard policy. Code: ${err.code}, message: ${err.message}`);
}
```


## securityManager.getAppClipboardPolicy

getAppClipboardPolicy(admin: Want | null, tokenId?: number): string

Obtains the device clipboard policy. Enterprises can use this API to query the current clipboard policy for policy audit and compliance check, ensuring that the clipboard policy complies with enterprise security requirements.

**Since:** 26.0.0

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SECURITY

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name     | Type                                      | Mandatory  | Description                      |
| -------- | ---------------------------------------- | ---- | ------------------------------- |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) \| null | Yes   | Enterprise Device Management Extension component. The Want must include the abilityName of the enterprise device management extension capability and the bundleName of the application.<br>When multiple MDM applications exist on the device, passing Want queries the policy set by the corresponding enterprise device management application, and passing null queries the policy that actually takes effect.|
| tokenId | number | No| Application token ID, which can be obtained using [bundleManager.getApplicationInfo](../apis-ability-kit/js-apis-bundleManager-applicationInfo.md).|

**Return value**

| Type                  | Description                     |
| --------------------- | ------------------------- |
| string | Device clipboard policy in JSON format.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                                      |
| ------- | ---------------------------------------------------------------------------- |
| 9200001 | The application is not an administrator application of the device.                        |
| 9200002 | The administrator application does not have permission to manage the device. |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { securityManager } from '@kit.MDMKit';

// Replace with actual values.
let tokenId: number = 586874394;
try {
  // Replace the parameters based on the actual situation.
  let result: string = securityManager.getAppClipboardPolicy(null, tokenId);
  console.info(`Succeeded in getting clipboard policy, result : ${result}`);
} catch (err) {
  console.error(`Failed to get clipboard policy. Code: ${err.code}, message: ${err.message}`);
}
```
## securityManager.setAppClipboardPolicy<sup>18+</sup>

setAppClipboardPolicy(admin: Want, bundleName: string, accountId: number, policy: ClipboardPolicy): void

Sets the device clipboard policy of a specified application for a specified user. After the policy is set, the clipboard of the specified application will be restricted in its usage scope according to the configured policy. Enterprises can configure differentiated clipboard usage permissions for different applications across different users, enabling fine-grained data access control and meeting the security management requirements in multi-user, multi-application scenarios.

> **NOTE**
>
> In a multi-MDM application scenario, the [strict control](../../mdm/mdm-kit-multi-mdm.md#rule-1-security-first) rule applies.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SECURITY

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name    | Type                                                     | Mandatory | Description                                                                                                                                                       |
| -------    | ------------------------------------------------------- | --- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| admin      | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.                                                                                                                                         |
| bundleName | string                                                  | Yes  | Bundle name of the application for which the device clipboard policy is set.                                                                                                                                     |
| accountId  | number                                                  | Yes  | User ID, which must be greater than or equal to 0. You can call [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1) of **@ohos.account.osAccount** to obtain the user ID.|
| policy     | [ClipboardPolicy](#clipboardpolicy)                     | Yes  | Clipboard policy to set.                                                                                                                                                   |

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message                                                                                                                                           |
| ------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 9200001 | The application is not an administrator application of the device.                                                                              |
| 9200002 | The administrator application does not have permission to manage the device.                                                                    |
| 201     | Permission verification failed. The application does not have the permission required to call the API.                                          |

**Example**

```ts
import { securityManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace with actual values.
let bundleName: string = 'com.example.myapplication';
let accountId: number = 100;
try {
  securityManager.setAppClipboardPolicy(wantTemp, bundleName, accountId, securityManager.ClipboardPolicy.IN_APP);
  console.info(`Succeeded in setting clipboard policy.`);
} catch (err) {
  console.error(`Failed to set clipboard policy. Code: ${err.code}, message: ${err.message}`);
}
```

## securityManager.getAppClipboardPolicy<sup>18+</sup>

getAppClipboardPolicy(admin: Want, bundleName: string, accountId: number): string

Obtains the device clipboard policy of a specified application under a specified user. Enterprises can use this API to query the clipboard usage permission configuration of a specific application for policy auditing and compliance checking.

This API queries the policy set by the corresponding enterprise device management application by passing in a Want. To query the policy that actually takes effect, use the [securityManager.getAppClipboardPolicy](#securitymanagergetappclipboardpolicy-2) API.

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name      | Type                                                      | Mandatory | Description                                                                                                                                                        |
| --------- | ------------------------------------------------------- | --------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes       | Enterprise device management extension component. The Want must include the abilityName of the enterprise device management extension capability and the bundleName of the application. |
| bundleName | string                                                  | Yes       | Bundle name of the application for which the clipboard policy is set.                                                                                          |
| accountId  | number                                                  | Yes       | User ID, which specifies a specific user. Value range: greater than or equal to 0. The accountId can be obtained through APIs such as [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1) in @ohos.account.osAccount. |

**Return value:**

| Type                                  | Description       |
| ----------------------------------- | -------- |
| string | JSON string of the device clipboard policy. |

**Error codes**

For details about the following error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID   | Error Information                                                                                                                                            |
| ------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 9200001 | The application is not an administrator application of the device.                                                                              |
| 9200002 | The administrator application does not have permission to manage the device.                                                                    |
| 201     | Permission verification failed. The application does not have the permission required to call the API.                                          |

**Example**

```ts
import { securityManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace it based on the actual situation.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace it based on the actual situation.
let bundleName: string = 'com.example.myapplication';
let accountId: number = 100;
try {
  let result: string = securityManager.getAppClipboardPolicy(wantTemp, bundleName, accountId);
  console.info(`Succeeded in getting clipboard policy, result : ${result}`);
} catch (err) {
  console.error(`Failed to get clipboard policy. Code: ${err.code}, message: ${err.message}`);
}
```


## securityManager.getAppClipboardPolicy

getAppClipboardPolicy(admin: Want | null, bundleName: string, accountId: number): string

Obtains the device clipboard policy of a specified application for a specified user. Enterprises can use this API to query the clipboard usage permission configuration of a specific application for policy audit and compliance check.

**Since:** 26.0.0

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SECURITY

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name    | Type                                                     | Mandatory | Description                                                                                                                                                       |
| -------    | ------------------------------------------------------- | --- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) \| null | Yes   | Enterprise device management extension component. The Want must include the abilityName of the enterprise device management extension capability and the bundleName of the application where it resides.<br>When multiple MDM applications exist on the device, passing in Want queries the policy set by the corresponding enterprise device management application, and passing in null queries the policy that actually takes effect.|
| bundleName | string                                                  | Yes  | Bundle name of the application for which the device clipboard policy is set.                                                                                                                           |
| accountId  | number                                                  | Yes  | User ID, which must be greater than or equal to 0. You can call [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1) of **@ohos.account.osAccount** to obtain the user ID.|

**Return value**

| Type                                 | Description      |
| ----------------------------------- | -------- |
| string | Device clipboard policy in JSON format.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message                                                                                                                                           |
| ------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 9200001 | The application is not an administrator application of the device.                                                                              |
| 9200002 | The administrator application does not have permission to manage the device.                                                                    |
| 201     | Permission verification failed. The application does not have the permission required to call the API.                                          |

**Example**

```ts
import { securityManager } from '@kit.MDMKit';

// Replace with actual values.
let bundleName: string = 'com.example.myapplication';
let accountId: number = 100;
try {
  // Replace the parameters based on the actual situation.
  let result: string = securityManager.getAppClipboardPolicy(null, bundleName, accountId);
  console.info(`Succeeded in getting clipboard policy, result : ${result}`);
} catch (err) {
  console.error(`Failed to get clipboard policy. Code: ${err.code}, message: ${err.message}`);
}
```
## securityManager.setWatermarkImage<sup>14+</sup>

setWatermarkImage(admin: Want, bundleName: string, source: string | image.PixelMap, accountId: number): void

Sets a watermark policy for a specified app of a specified user. Currently, a maximum of 100 policies can be saved.
> **NOTE**
>
> 1. This API is used in enterprise scenarios to set a watermark for third-party apps, reducing the risk of enterprise information leakage. It is not recommended to set a watermark for system apps (for example, the home screen app), as unknown exceptions may occur.
>
> 2. The watermark image is tiled repeatedly to cover the entire app UI.
>
> 3. In a multi-MDM application scenario, the watermark of the same app under the same user follows the [exclusive](../../mdm/mdm-kit-multi-mdm.md#rule-2-policy-exclusivity) rule. The watermarks of different users and different apps follow the [merge](../../mdm/mdm-kit-multi-mdm.md#rule-4-policy-merging) rule.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SECURITY

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name     | Type                                      | Mandatory  | Description                      |
| -------- | ---------------------------------------- | ---- | ------------------------------- |
| admin    | [Want](../apis-ability-kit/js-apis-app-ability-want.md)     | Yes   | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.     |
| bundleName | string    | Yes  | Bundle name of the application for which the watermark is set.                                                      |
| source | string \| [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md)  | Yes  | **string** indicates the image path, which is the path that the app has the permission to access, such as the app sandbox path. For details about the mapping between the app sandbox path and the actual physical path, see [Mappings Between App Sandbox Paths and Physical Paths](../../file-management/app-sandbox-directory.md#mappings-between-application-sandbox-paths-and-physical-paths).<br>**image.PixelMap** indicates the image object.<br>The size of the image pixel data cannot exceed 500 KB.<br>The size of the image pixel data is calculated as follows: Image width (pixels) × Image height (pixels) × Number of bytes per pixel (typically 4). For example, the size of a 100 × 100 image is 100 × 100 × 4 = 40,000 bytes.                                                      |
| accountId     | number     | Yes  | User ID. You can call [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1) of **@ohos.account.osAccount** to obtain the user ID.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                                      |
| ------- | ---------------------------------------------------------------------------- |
| 9200001 | The application is not an administrator application of the device.                        |
| 9200002 | The administrator application does not have permission to manage the device. |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { securityManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace with actual values.
let bundleName: string = 'com.example.myapplication';
let source: string = '/data/storage/el1/base/test.png';
let accountId: number = 100;
try {
  securityManager.setWatermarkImage(wantTemp, bundleName, source, accountId);
  console.info(`Succeeded in setting watermarkImage policy.`);
} catch (err) {
  console.error(`Failed to set watermarkImage policy. Code: ${err.code}, message: ${err.message}`);
}
```

## securityManager.cancelWatermarkImage<sup>14+</sup>

cancelWatermarkImage(admin: Want, bundleName: string, accountId: number): void

Cancels the watermark policy for a specified user. When an application no longer requires watermark protection or needs to be updated, enterprises can call this API to cancel the watermark policy.<!--RP4--><!--RP4End-->

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SECURITY

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name     | Type                                      | Mandatory  | Description                      |
| -------- | ---------------------------------------- | ---- | ------------------------------- |
| admin    | [Want](../apis-ability-kit/js-apis-app-ability-want.md)     | Yes   | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.       |
| bundleName | string    | Yes  | Bundle name of the application for which the watermark is removed.                                                      |
| accountId     | number     | Yes  | User ID. You can call [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1) of **@ohos.account.osAccount** to obtain the user ID.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                                      |
| ------- | ---------------------------------------------------------------------------- |
| 9200001 | The application is not an administrator application of the device.                        |
| 9200002 | The administrator application does not have permission to manage the device. |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { securityManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace with actual values.
let bundleName: string = 'com.example.myapplication';
let accountId: number = 100;
try {
  securityManager.cancelWatermarkImage(wantTemp, bundleName, accountId);
  console.info(`Succeeded in cancelling watermarkImage policy.`);
} catch (err) {
  console.error(`Failed to cancel watermarkImage policy. Code: ${err.code}, message: ${err.message}`);
}
```

## securityManager.setPermissionManagedState<sup>20+</sup>

setPermissionManagedState(admin: Want, applicationInstance: ApplicationInstance, permissions: Array\<string>, managedState: PermissionManagedState): void

Sets the management policy for the [user_grant permission](../../security/AccessToken/permissions-for-all-user.md) of a specified application. This is applicable to enterprise application batch deployment scenarios, such as granting permissions silently to reduce permission prompt interruptions, and unifying permission management policies for enterprise applications, thereby improving employee user experience and management efficiency.

> **NOTE**
>
> In a multi-MDM application scenario, the same permission of the same app instance is [exclusive](../../mdm/mdm-kit-multi-mdm.md#rule-2-policy-exclusivity), and different permissions of different app instances are [merged](../../mdm/mdm-kit-multi-mdm.md#rule-4-policy-merging).

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_USER_GRANT_PERMISSION

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name     | Type                                      | Mandatory  | Description                      |
| -------- | ---------------------------------------- | ---- | ------------------------------- |
| admin    | [Want](../apis-ability-kit/js-apis-app-ability-want.md)     | Yes   | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.     |
| applicationInstance    | [ApplicationInstance](#applicationinstance20)  | Yes| Application instance.|
| permissions | Array&lt;string&gt;  | Yes| List of permissions to be managed. Only [user_grant permission](../../security/AccessToken/permissions-for-all-user.md) is supported. The list is grouped by [application permission groups](../../security/AccessToken/app-permission-group-list.md) and must include all permissions in the same permission group declared by the application in [module.json5](../../quick-start/module-configuration-file.md). For example, if an application declares ohos.permission.READ_CALENDAR and ohos.permission.WRITE_CALENDAR in **module.json5**, the input permission list must contain both ohos.permission.READ_CALENDAR and ohos.permission.WRITE_CALENDAR.|
| managedState | [PermissionManagedState](#permissionmanagedstate20) | Yes| Management policy for application permissions.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                                      |
| ------- | ---------------------------------------------------------------------------- |
| 9200001 | The application is not an administrator application of the device.                        |
| 9200002 | The administrator application does not have permission to manage the device. |
| 9200010 | A conflict policy has been configured. |
| 9200012 | Parameter verification failed. |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { Want } from '@kit.AbilityKit';
import { securityManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
let appInstanceTemp: securityManager.ApplicationInstance = {
  // Replace with actual values.
  appIdentifier: '736498586',
  appIndex: 0,
  accountId: 100
};
let permissionsTemp: Array<string> = ['ohos.permission.CAMERA', 'ohos.permission.LOCATION'];
try {
  securityManager.setPermissionManagedState(wantTemp, appInstanceTemp, permissionsTemp,
    securityManager.PermissionManagedState.GRANTED);
  console.info('Succeeded in setting permission managed state.');
} catch (err) {
  console.error(`Failed to set permission managed state.  Code: ${err.code}, message: ${err.message}`);
}
```

## securityManager.getPermissionManagedState<sup>20+</sup>

getPermissionManagedState(admin: Want, applicationInstance: ApplicationInstance, permission: string): PermissionManagedState

Obtains the management policy for the [user_grant permission](../../security/AccessToken/permissions-for-all-user.md) of a specified application.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_USER_GRANT_PERMISSION

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name     | Type                                      | Mandatory  | Description                      |
| -------- | ---------------------------------------- | ---- | ------------------------------- |
| admin    | [Want](../apis-ability-kit/js-apis-app-ability-want.md)     | Yes   | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.     |
| applicationInstance  | [ApplicationInstance](#applicationinstance20)  | Yes| Application instance.|
| permission | string | Yes| Name of the permission required for obtaining the management policy. Only the **user_grant** permission is supported.|

**Return value**

| Type                  | Description                     |
| --------------------- | ------------------------- |
| [PermissionManagedState](#permissionmanagedstate20) | Management policy for application permissions.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                                      |
| ------- | ---------------------------------------------------------------------------- |
| 9200001 | The application is not an administrator application of the device.                        |
| 9200002 | The administrator application does not have permission to manage the device. |
| 9200012 | Parameter verification failed. |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { Want } from '@kit.AbilityKit';
import { securityManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
let appInstanceTemp: securityManager.ApplicationInstance = {
  // Replace with actual values.
  appIdentifier: '736498586',
  appIndex: 0,
  accountId: 100
};
let permissionTemp: string = 'ohos.permission.ENTERPRISE_MANAGE_USER_GRANT_PERMISSION';
try {
  let result: securityManager.PermissionManagedState =
    securityManager.getPermissionManagedState(wantTemp, appInstanceTemp, permissionTemp);
  console.info(`Succeeded in getting permission managed state, result : ${result}`);
} catch (err) {
  console.error(`Failed to get permission managed state. Code: ${err.code}, message: ${err.message}`);
}
```

## securityManager.setExternalSourceExtensionsPolicy<sup>22+</sup>

setExternalSourceExtensionsPolicy(admin: Want, policy: common.ManagedPolicy): void

Sets the management policy for extensions from external sources. After the policy is set, the system controls the running behavior of extensions from external sources based on the configured policy. This API is applicable to enterprise security management scenarios, such as preventing employees from installing unauthorized browser extensions or forcibly enabling enterprise-approved extension functions to ensure enterprise device security.

- DEFAULT:

  Default policy with no restrictions applied. Users can enable or disable **Run extensions from external sources** in **Settings** > **Privacy & security** > **Advanced option**.

- DISALLOW:

  Policy that disallows extensions from external sources to run. With this policy, currently running extensions can continue, but cannot be started after being closed. Users cannot enable **Run extensions from external sources**.

- FORCE_OPEN:

  Policy that forcibly enables extensions from external sources to run. Users cannot disable **Run extensions from external sources**.

> **NOTE**
>
> In a multi-MDM application scenario, the [exclusive](../../mdm/mdm-kit-multi-mdm.md#rule-2-policy-exclusivity) rule applies.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SECURITY

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences**: This API can be properly called on PCs/2-in-1 devices. If it is called on other device types, error code 801 is returned.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name    | Type                                                     | Mandatory | Description                                                                                                                                                       |
| -------    | ------------------------------------------------------- | --- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| admin      | [Want](../apis-ability-kit/js-apis-app-ability-want.md#want) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.                                                                                                                                         |
| policy     | [common.ManagedPolicy](../apis-mdm-kit/js-apis-enterprise-common.md#managedpolicy)                     | Yes  | Management policy.                                                                                                                                                   |

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message                                                                                                                                           |
| ------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 9200001 | The application is not an administrator application of the device.                                                                              |
| 9200002 | The administrator application does not have permission to manage the device.                                                                    |
| 9200010 | A conflict policy has been configured.                                          |
| 9200012 | Parameter verification failed.                                          |
| 201     | Permission verification failed. The application does not have the permission required to call the API.                                          |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**Example**

```ts
import { common, securityManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
try {
  securityManager.setExternalSourceExtensionsPolicy(wantTemp, common.ManagedPolicy.FORCE_OPEN);
  console.info(`Succeeded in setting managed policy.`);
} catch (err) {
  console.error(`Failed to set managed policy. Code: ${err.code}, message: ${err.message}`);
}
```

## securityManager.getExternalSourceExtensionsPolicy<sup>22+</sup>

getExternalSourceExtensionsPolicy(admin: Want): common.ManagedPolicy

Obtains the management policy of external source extensions.

This API queries the policy set by the corresponding enterprise device management application by passing in a Want. To query the policy that actually takes effect, use the [securityManager.getExternalSourceExtensionsPolicy](#securitymanagergetexternalsourceextensionspolicy) API.

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences**: This API can be properly called only on PCs/2-in-1 devices. On other devices, it returns the error code 801.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name     | Type                                                      | Mandatory  | Description                                                                                                                                                        |
| -------    | ------------------------------------------------------- | --- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes   | Enterprise device management extension component. The Want must include the abilityName of the enterprise device management extension capability and the bundleName of the application. |

**Return value**

| Type                                  | Description       |
| ----------------------------------- | -------- |
|  [common.ManagedPolicy](../apis-mdm-kit/js-apis-enterprise-common.md#managedpolicy) | Returns the management policy of the ManagedPolicy enum type. |

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID   | Error Message                                                                                                                                            |
| ------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 9200001 | The application is not an administrator application of the device.                                                                              |
| 9200002 | The administrator application does not have permission to manage the device.                                                                    |
| 201     | Permission verification failed. The application does not have the permission required to call the API.                                          |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**Example**

```ts
import { common, securityManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace it based on the actual situation.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  let result: common.ManagedPolicy = securityManager.getExternalSourceExtensionsPolicy(wantTemp);
  console.info(`Succeeded in getting managed policy, result : ${result}`);
} catch (err) {
  console.error(`Failed to get managed policy. Code: ${err.code}, message: ${err.message}`);
}
```


## securityManager.getExternalSourceExtensionsPolicy

getExternalSourceExtensionsPolicy(admin: Want | null): common.ManagedPolicy

Obtains the management policy for extensions from external sources.

**Since:** 26.0.0

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SECURITY

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences**: This API can be properly called on PCs/2-in-1 devices. If it is called on other device types, error code 801 is returned.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name    | Type                                                     | Mandatory | Description                                                                                                                                                       |
| -------    | ------------------------------------------------------- | --- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) \| null | Yes   | Enterprise Device Management Extension. The Want must include the abilityName of the enterprise device management extension capability and the bundleName of the application where it resides.<br>When multiple MDM applications exist on the device, passing Want queries the policy set by the corresponding enterprise device management application, while passing null queries the policy that actually takes effect.|

**Return value**

| Type                                 | Description      |
| ----------------------------------- | -------- |
|  [common.ManagedPolicy](../apis-mdm-kit/js-apis-enterprise-common.md#managedpolicy) | Management policy obtained.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID  | Error Message                                                                                                                                           |
| ------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 9200001 | The application is not an administrator application of the device.                                                                              |
| 9200002 | The administrator application does not have permission to manage the device.                                                                    |
| 201     | Permission verification failed. The application does not have the permission required to call the API.                                          |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**Example**

```ts
import { common, securityManager } from '@kit.MDMKit';

try {
  // Replace the parameters based on the actual situation.
  let result: common.ManagedPolicy = securityManager.getExternalSourceExtensionsPolicy(null);
  console.info(`Succeeded in getting managed policy, result : ${result}`);
} catch (err) {
  console.error(`Failed to get managed policy. Code: ${err.code}, message: ${err.message}`);
}
```
## securityManager.installEnterpriseReSignatureCertificate<sup>24+</sup>

installEnterpriseReSignatureCertificate(admin: Want, certificateAlias: string, fd: number, accountId: number): void

Installs the enterprise application re-signing certificate. After the installation is successful, the enterprise can use the certificate to re-sign applications.

A maximum of 10 distinct certificates can be deployed per user. The certificate alias serves as a unique identifier for each certificate and cannot be duplicated during deployment. To update a certificate with an existing alias, you must first uninstall the old certificate by calling [uninstallEnterpriseReSignatureCertificate](#securitymanageruninstallenterpriseresignaturecertificate24).

The installed certificates are retained on the device and will not be removed when the MDM app is uninstalled or the admin privilege is deactivated.

In the enterprise app distribution scenario, <!--RP2--><!--RP2End-->you can use the re-signing certificate to re-sign enterprise apps. After re-signing, the app package is provided to enterprise administrators, who can then install the re-signed app on enterprise devices where the corresponding re-signing certificate has been deployed.

Process of using the enterprise application re-signing certificate:<!--RP3--><!--RP3End--><br>1. Install the enterprise application re-signing certificate through the MDM application.<br>2. Re-sign the original HAP package using a signing tool (**ohos-signer** or the DevEco Studio signing plugin).<br>3. Install the re-signed app (through the enterprise private app store).<br>4. Launch and run the app.

Specifications:<br>1. Apps signed with the old certificate will continue to run normally after a new re-signing certificate is installed.<br>2. After a new enterprise signing certificate is installed for an installed enterprise app, if the installed app needs to be updated, you can directly overwrite the original app without uninstalling it.<br>3. In enterprise scenarios (especially those involving information security), enterprises need to ensure that only designated internal software and tools are installed and run on employees' mobile devices. The enterprise application re-signing certificate, in conjunction with the system's application management and permission control mechanisms (via a unified application ID), supports silent installation of enterprise applications, controlled invocation of system capabilities, and restriction of application running scopes. This enables admission control and security governance for enterprise software on managed devices.

> **NOTE**
>
> In multiple MDM application scenarios, follow the [configuration](../../mdm/mdm-kit-multi-mdm.md#rule-3-latest-configuration-precedence) rule.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SECURITY

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name     | Type                                                   | Mandatory| Description          |
| ----------- | ------------------------------------------------------- | ---- | -------------- |
| admin | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes| EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|
| certificateAlias | string | Yes| Certificate alias, which must end with **.cer**.|
| fd | number | Yes| Descriptor of an existing re-signing certificate file. The certificate file must be stored in the [app sandbox directory](../../file-management/app-sandbox-directory.md).|
| accountId | number | Yes| User ID, which must be greater than or equal to 0. You can call [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1) of **@ohos.account.osAccount** to obtain the user ID.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200012  | Parameter verification failed. |
| 9201006  | The number of certificates has reached the limit. |
| 9201007  | The certificate is invalid. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { securityManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';
import { fileIo } from '@kit.CoreFileKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// The test.cer certificate file must be placed in the application sandbox and be a valid enterprise application re-signing certificate.
// Replace with actual values.
const filePath = '/test.cer';
// Replace with actual values.
let certificateAlias: string = 'test.cer';
let fd: number = fileIo.openSync(filePath, fileIo.OpenMode.READ_ONLY).fd;
// Replace with actual values.
let accountId: number = 100;
try {
  securityManager.installEnterpriseReSignatureCertificate(
    wantTemp, certificateAlias, fd, accountId);
  console.info('Success in installing enterprise re signature certificate.');
} catch (err) {
  console.error(`Failed to install enterprise re signature certificate.
    Code: ${err.code}, message: ${err.message}`);
};
```

## securityManager.uninstallEnterpriseReSignatureCertificate<sup>24+</sup>

uninstallEnterpriseReSignatureCertificate(admin: Want, certificateAlias: string, accountId: number): void

Uninstalls the enterprise application re-signing certificate. After the enterprise re-signing certificate is uninstalled, the applications signed using this certificate can run properly before the device is restarted, but cannot run after the device is restarted.

Usage scenarios:<br>1. Installing a new certificate: After a new certificate is installed via the [installEnterpriseReSignatureCertificate](#securitymanagerinstallenterpriseresignaturecertificate24) API, applications re-signed using the new certificate can run properly. If the application corresponding to the old signing certificate is a super device administrator application, the application must be deactivated before the certificate can be uninstalled. Otherwise, after the certificate is uninstalled, the application cannot be uninstalled or run.<br>2. Restoring a mistakenly deleted certificate: After a mistakenly deleted certificate is re-installed via the [installEnterpriseReSignatureCertificate](#securitymanagerinstallenterpriseresignaturecertificate24) API, re-signed applications can run normally without being affected.

> **NOTE**
>
> Certificate deletion is typically performed in scenarios such as certificate expiration or certificate leakage. You are advised to implement this feature with a strong prompt to administrators, advising them to delete certificates with caution. Before deleting a certificate, ensure that a new re-signing certificate has been loaded and that all applications have been updated and switched to the new re-signing certificate. Otherwise, historically installed applications will fail to run after a device restart.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SECURITY

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name     | Type                                                   | Mandatory| Description          |
| ----------- | ------------------------------------------------------- | ---- | -------------- |
| admin | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes| EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|
| certificateAlias | string | Yes| Certificate alias, which must end with **.cer**.|
| accountId | number | Yes| User ID, which must be greater than or equal to 0. You can call [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1) of **@ohos.account.osAccount** to obtain the user ID.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200012  | Parameter verification failed. |
| 9201008  | The certificate does not exist. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { securityManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace with actual values.
let certificateAlias: string = 'test.cer';
// Replace with actual values.
let accountId: number = 100;
try {
  securityManager.uninstallEnterpriseReSignatureCertificate(
    wantTemp, certificateAlias, accountId);
  console.info('Success in uninstalling enterprise re signature certificate.');
} catch (err) {
  console.error(`Failed to uninstall enterprise re signature certificate.
    Code: ${err.code}, message: ${err.message}`);
};
```

## securityManager.setScreenWatermarkImage

setScreenWatermarkImage(admin: Want, pixelMap: image.PixelMap): void

Sets a screen watermark policy, which takes effect for all users.

> **NOTE**
>
> 1. The screen watermark policy tiles the configured image to cover the entire screen. It is recommended to use an image with transparency to ensure that the screen content remains visible.
>
> 2. When the watermark image is smaller than the screen, the image is stretched; when the watermark image is larger than the screen, the image is compressed. This implementation differs from the repeated tiling method used for application-level watermarks.
>
> 3. In multiple MDM application scenarios, follow the [configuration](../../mdm/mdm-kit-multi-mdm.md#rule-3-latest-configuration-precedence) rule.

**Since:** 26.0.0

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SECURITY

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name     | Type                                      | Mandatory  | Description                      |
| -------- | ---------------------------------------- | ---- | ------------------------------- |
| admin    | [Want](../apis-ability-kit/js-apis-app-ability-want.md)     | Yes   | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.     |
| pixelMap | [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md)  | Yes  | Image object. The image width must not exceed twice the screen width, and the image height must not exceed twice the screen height. The size of the image pixel data cannot exceed 128 MB. The size of the image pixel data is calculated as follows: Image width (pixels) × Image height (pixels) × Number of bytes per pixel (typically 4). For example, the size of a 100 × 100 image is 100 × 100 × 4 = 40,000 bytes. For a 1920 × 1080 screen, using an image of the same resolution results in a pixel data size of 1920 × 1080 × 4 = 8,294,400 bytes (approximately 7.9 MB).                                                      |

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                                      |
| ------- | ---------------------------------------------------------------------------- |
| 9200001 | The application is not an administrator application of the device.                        |
| 9200002 | The administrator application does not have permission to manage the device. |
| 9200012 | Parameter verification failed. |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { securityManager } from '@kit.MDMKit';
import { common, Want } from '@kit.AbilityKit';
import { image } from '@kit.ImageKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
const context = this.getUIContext().getHostContext() as common.UIAbilityContext;
// 'test.png' is only an example. Replace it with the actual one.
const path: string = context.filesDir + "/test.png";
// Create an ImageSource.
const imageSource: image.ImageSource = image.createImageSource(path);
// Create a PixelMap.
imageSource.createPixelMap().then((pixelMap: image.PixelMap) => {
  try {
    securityManager.setScreenWatermarkImage(wantTemp, pixelMap);
    console.info(`Succeeded in setting screen watermark image.`);
  } catch (err) {
    console.error(`Failed to set screen watermark image. Code: ${err.code}, message: ${err.message}`);
  }
}).catch((err: Error) => {
  console.error(`Failed to create PixelMap. message: ${err.message}`);
});
```

## securityManager.cancelScreenWatermarkImage

cancelScreenWatermarkImage(admin: Want): void

Cancels a screen watermark policy, which takes effect for all users. After the cancellation is successful, the watermark on the device screen disappears. When a device no longer requires screen watermark protection, enterprises can call this API to cancel the watermark policy. Only the user who sets the screen watermark can cancel it. For example, user 101 cannot cancel the screen mark set by user 100

**Since:** 26.0.0

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SECURITY

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name     | Type                                      | Mandatory  | Description                      |
| -------- | ---------------------------------------- | ---- | ------------------------------- |
| admin    | [Want](../apis-ability-kit/js-apis-app-ability-want.md)     | Yes   | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.       |

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                                      |
| ------- | ---------------------------------------------------------------------------- |
| 9200001 | The application is not an administrator application of the device.                        |
| 9200002 | The administrator application does not have permission to manage the device. |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { securityManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
try {
    securityManager.cancelScreenWatermarkImage(wantTemp);
    console.info(`Succeeded in canceling screen watermark image.`);
} catch (err) {
    console.error(`Failed to cancel screen watermark image. Code: ${err.code}, message: ${err.message}`);
}
```

## securityManager.setDisallowedPermission

setDisallowedPermission(admin: Want, permission: string, disallow: boolean, accountId: number): void

Disables the specified permission of the specified user. After the permission is disabled, all applications under the specified user will be denied by default when applying for or using the specified permission. This API is applicable to enterprise security compliance scenarios, such as disabling high-risk permissions like camera and microphone to prevent privacy leaks, or disabling specific features (such as Bluetooth sharing) to prevent enterprise data from being transferred out.

> **NOTE**
>
> 1. Only permissions whose [permission APL](../../security/AccessToken/app-permission-mgmt-overview.md#basic-concepts-in-the-permission-mechanism) is normal or system_basic can be disabled. Otherwise, error code 9201045 is returned.
>
> 2. A maximum of 200 permissions can be disabled for a single user.
>
> 3. After a permission is disabled, only the use of the corresponding permission by applications (system applications and common applications) is affected. The use of the corresponding permission by system SAs is not affected.
>
> 4. In multiple MDM application scenarios, [strict control](../../mdm/mdm-kit-multi-mdm.md#rule-1-security-first) applies to the same permission, and [merging](../../mdm/mdm-kit-multi-mdm.md#rule-4-policy-merging) applies to different permissions.

**Since:** 26.0.0

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SECURITY

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name     | Type                                                   | Mandatory| Description          |
| ----------- | ------------------------------------------------------- | ---- | -------------- |
| admin       | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|
| permission  | string                                                  | Yes  | Name of the permission.|
| disallow    | boolean                                                 | Yes  | Whether to disable the permission. The value **true** indicates yes, and the value **false** indicates no.|
| accountId   | number                                                  | Yes  | User ID, which must be greater than or equal to 0. You can call [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1) of **@ohos.account.osAccount** to obtain the user ID.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200012  | Parameter verification failed. |
| 9201045  | This permission cannot be disallowed. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { securityManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace with actual values.
let permission: string = 'ohos.permission.CAMERA';
let disallow: boolean = true;
let accountId: number = 100;
try {
  securityManager.setDisallowedPermission(wantTemp, permission, disallow, accountId);
  console.info(`Succeeded in setting disallowed permission.`);
} catch (err) {
  console.error(`Failed to set disallowed permission. Code: ${err.code}, message: ${err.message}`);
}
```

## securityManager.getDisallowedPermissions

getDisallowedPermissions(admin: Want | null, accountId: number): Array\<string\>

Obtains the list of disabled permissions of a specified user.

**Since:** 26.0.0

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SECURITY

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name     | Type                                                   | Mandatory| Description          |
| ----------- | ------------------------------------------------------- | ---- | -------------- |
| admin       | [Want](../apis-ability-kit/js-apis-app-ability-want.md) \| null | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. If the **admin** is **null**, the list of disabled permissions delivered by all enterprise device administrator applications is obtained, and the merged result is returned.|
| accountId   | number                                                  | Yes  | User ID, which must be greater than or equal to 0. You can call [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1) of **@ohos.account.osAccount** to obtain the user ID.|

**Return value**

| Type  | Description                |
| ------ | -------------------- |
| Array&lt;string&gt; | List of disabled permissions.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200012  | Parameter verification failed. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { securityManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace with actual values.
let accountId: number = 100;
try {
  let result: Array<string> = securityManager.getDisallowedPermissions(wantTemp, accountId);
  console.info(`Succeeded in getting disallowed permissions, result : ${JSON.stringify(result)}`);
} catch (err) {
  console.error(`Failed to get disallowed permissions. Code: ${err.code}, message: ${err.message}`);
}
```

## securityManager.addAllowedPermissionBundle

addAllowedPermissionBundle(admin: Want, permission: string, applicationInstance: common.ApplicationInstance): void

Adds an application to the permission usage exception list. Applications in the list are not subject to the permission restriction policy set via [setDisallowedPermission](#securitymanagersetdisallowedpermission). This API is applicable to enterprise scenarios. For example, when the camera permission is disabled, attendance applications and collaborative office applications can still use the camera, ensuring that critical enterprise business operates normally.

> **NOTE**
>
> 1. You must first disable a permission through [setDisallowedPermission](#securitymanagersetdisallowedpermission) before adding an application to the permission usage exception list. Otherwise, error code 9201044 is returned.
>
> 2. An application cannot be added to the permission usage exception list if it has not actually requested the specified permission. For example, when the camera permission is disabled and application A has not actually requested the camera permission, application A cannot be added to the camera permission usage exception list, and error code 9200012 is returned. You can use the [bm dump](../../tools/bm-tool.md#dump) command to query whether an application has requested a specified permission.
>
> 3. When a specified permission is re-enabled through [setDisallowedPermission](#securitymanagersetdisallowedpermission), the permission usage exception list corresponding to that permission is cleared synchronously.
>
> 4. A maximum of 1024 applications can be added to the permission usage exception list for a single permission across all users.
>
> 5. Both system applications and common applications can be added.
>
> 6. In multiple MDM application scenarios, follow the [merging](../../mdm/mdm-kit-multi-mdm.md#rule-4-policy-merging) rule.

**Since:** 26.0.0

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SECURITY

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name     | Type                                                   | Mandatory| Description          |
| ----------- | ------------------------------------------------------- | ---- | -------------- |
| admin       | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|
| permission  | string                                                  | Yes  | Name of the permission.|
| applicationInstance | [common.ApplicationInstance](./js-apis-enterprise-common.md#applicationinstance) | Yes  | Information about the application instance to be added to the permission exception list.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200012  | Parameter verification failed. |
| 9201015  | The application is not installed. |
| 9201044  | This permission is not disallowed. Applications cannot be added to or removed from the trustlist. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { securityManager, common } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace with actual values.
let permission: string = 'ohos.permission.CAMERA';
let disallow: boolean = true;
let accountId: number = 100;
// The application has requested the ohos.permission.CAMERA permission.
let appInstance: common.ApplicationInstance = {
  appIdentifier: '123456789',
  appIndex: 0,
  accountId: 100
};
try {
  // Disable the ohos.permission.CAMERA permission.
  securityManager.setDisallowedPermission(wantTemp, permission, disallow, accountId);
  // Set a specified application to continue using the ohos.permission.CAMERA permission.
  securityManager.addAllowedPermissionBundle(wantTemp, permission, appInstance);
  console.info(`Succeeded in adding allowed permission bundle.`);
} catch (err) {
  console.error(`Failed to add allowed permission bundle. Code: ${err.code}, message: ${err.message}`);
}
```

## securityManager.removeAllowedPermissionBundle

removeAllowedPermissionBundle(admin: Want, permission: string, applicationInstance: common.ApplicationInstance): void

Removes an application from the permission usage exception list. After the application is removed, it cannot use the corresponding permission any more.

> **NOTE**
>
> You must first disable a permission through [setDisallowedPermission](#securitymanagersetdisallowedpermission) before removing an application from the permission usage exception list. Otherwise, error code 9201044 is returned.
>
> In multiple MDM application scenarios, follow the [merging](../../mdm/mdm-kit-multi-mdm.md#rule-4-policy-merging) rule.

**Since:** 26.0.0

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SECURITY

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name     | Type                                                   | Mandatory| Description          |
| ----------- | ------------------------------------------------------- | ---- | -------------- |
| admin       | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|
| permission  | string                                                  | Yes  | Name of the permission.|
| applicationInstance | [common.ApplicationInstance](./js-apis-enterprise-common.md#applicationinstance) | Yes  | Information about the application instance to be removed from the permission exception list.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200012  | Parameter verification failed. |
| 9201044  | This permission is not disallowed. Applications cannot be added to or removed from the trustlist. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { securityManager, common } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace with actual values.
let permission: string = 'ohos.permission.CAMERA';
let appInstance: common.ApplicationInstance = {
  appIdentifier: '736498586',
  appIndex: 0,
  accountId: 100
};
try {
  securityManager.removeAllowedPermissionBundle(wantTemp, permission, appInstance);
  console.info(`Succeeded in removing allowed permission bundle.`);
} catch (err) {
  console.error(`Failed to remove allowed permission bundle. Code: ${err.code}, message: ${err.message}`);
}
```

## securityManager.getAllowedPermissionBundles

getAllowedPermissionBundles(admin: Want | null, permission: string, accountId: number): Array\<common.ApplicationInstance\>

Obtains the list of applications in the permission exception list.

**Since:** 26.0.0

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SECURITY

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name     | Type                                                   | Mandatory| Description          |
| ----------- | ------------------------------------------------------- | ---- | -------------- |
| admin       | [Want](../apis-ability-kit/js-apis-app-ability-want.md) \| null | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. If the **admin** is **null**, the list of applications in the permission exception list delivered by all enterprise device administrator applications is obtained, and the merged result is returned.|
| permission  | string                                                  | Yes  | Name of the permission.|
| accountId   | number                                                  | Yes  | User ID, which must be greater than or equal to 0. You can call [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1) of **@ohos.account.osAccount** to obtain the user ID.|

**Return value**

| Type  | Description                |
| ------ | -------------------- |
| Array&lt;[common.ApplicationInstance](./js-apis-enterprise-common.md#applicationinstance)&gt; | List of applications in the permission exception list.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200012  | Parameter verification failed. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { securityManager, common } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace with actual values.
let permission: string = 'ohos.permission.CAMERA';
let accountId: number = 100;
try {
  let result: Array<common.ApplicationInstance> =
    securityManager.getAllowedPermissionBundles(wantTemp, permission, accountId);
  console.info(`Succeeded in getting allowed permission bundles, result : ${JSON.stringify(result)}`);
} catch (err) {
  console.error(`Failed to get allowed permission bundles. Code: ${err.code}, message: ${err.message}`);
}
```

## securityManager.setWatermarkImage

setWatermarkImage(admin: Want, bundleName: string, source: string | image.PixelMap, accountId: number, properties:WatermarkProperties): void

Sets a watermark policy for a specified application of a specified user. Currently, a maximum of 100 policies can be saved.

> **NOTE**
>
> This API is used to set a watermark for third-party applications in enterprise scenarios to reduce the risk of enterprise information leakage. It is not recommended to set a watermark for system applications (such as the home screen application), as unknown exceptions may occur.
>
> The row and column parameters of the watermark attribute [properties](#watermarkproperties) must be integers in the range [1, 255]. If a value less than 1 or greater than 255 is passed in, the API returns error code 9200012.
>
> When both the number of rows and the number of columns of the watermark attribute are 1, a single watermark image is displayed in the center. When the number of rows is m and the number of columns is n, m\*n watermark images are displayed in an m-by-n grid layout. When the row and column parameters of the watermark attribute are too large, causing the grid layout to be unable to fit the window size, the watermark is tiled repeatedly from the upper left corner of the window to cover the entire application window, and the parts of the watermark image beyond the right and bottom edges of the window are cropped. For example, if the screen width and height are 1260\*2720 and the watermark image width and height are 100\*100, and the number of rows set exceeds 27 or the number of columns set exceeds 12, the watermark is tiled repeatedly to cover the entire application window.
>
> In multiple MDM application scenarios, the watermark of the same application under the same user follows the [exclusive](../../mdm/mdm-kit-multi-mdm.md#rule-2-policy-exclusivity) rule. The watermarks of different users and different applications follow the [merging](../../mdm/mdm-kit-multi-mdm.md#rule-4-policy-merging) rule.

**Since:** 26.0.0

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SECURITY

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name     | Type                                      | Mandatory  | Description                      |
| -------- | ---------------------------------------- | ---- | ------------------------------- |
| admin    | [Want](../apis-ability-kit/js-apis-app-ability-want.md)     | Yes   | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.     |
| bundleName | string    | Yes  | Bundle name of the application for which the watermark is set.                                                      |
| source | string \| [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md)  | Yes  | **string** indicates the image path, which is the path that the app has the permission to access, such as the app sandbox path. For details about the mapping between the app sandbox path and the actual physical path, see [Mappings Between App Sandbox Paths and Physical Paths](../../file-management/app-sandbox-directory.md#mappings-between-application-sandbox-paths-and-physical-paths).<br>**image.PixelMap** indicates the image object.<br>The size of the image pixel data cannot exceed 500 KB.<br>The size of the image pixel data is calculated as follows: Image width (pixels) × Image height (pixels) × Number of bytes per pixel (typically 4). For example, the size of a 100 × 100 image is 100 × 100 × 4 = 40,000 bytes.                                                      |
| accountId     | number     | Yes  | User ID, which must be greater than or equal to 0. You can call [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1) of **@ohos.account.osAccount** to obtain the user ID.|
| properties     | [WatermarkProperties](#watermarkproperties)     | Yes  | Number of rows and columns for the watermark.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                                      |
| ------- | ---------------------------------------------------------------------------- |
| 9200001 | The application is not an administrator application of the device.                        |
| 9200002 | The administrator application does not have permission to manage the device. |
| 9200012  | Parameter verification failed. |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { securityManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace with actual values.
let bundleName: string = 'com.example.myapplication';
let source: string = '/data/storage/el1/base/test.png';
let accountId: number = 100;
// Set them with actual values. In the sample code, the number of rows and the number of columns are both set to 1 for the watermark, and a single watermark image is displayed in the center.
let properties: securityManager.WatermarkProperties = {
  intervalsRow: 1,
  intervalsCol: 1
};
try {
  securityManager.setWatermarkImage(wantTemp, bundleName, source, accountId, properties);
  console.info(`Succeeded in setting watermarkImage policy.`);
} catch (err) {
  console.error(`Failed to set watermarkImage policy. Code: ${err.code}, message: ${err.message}`);
}
```

```ts
import { securityManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace with actual values.
let bundleName: string = 'com.example.myapplication';
let source: string = '/data/storage/el1/base/test.png';
let accountId: number = 100;
// Set them with actual values. The device screen size is 1260 × 2720, and the watermark image size is 100 × 100. In this example, the watermark properties are set to 27 rows and 12 columns, displaying 27 × 12 watermark images in a 27-row by 12-column grid layout.
let properties: securityManager.WatermarkProperties = {
  intervalsRow: 27,
  intervalsCol: 12
};
try {
  securityManager.setWatermarkImage(wantTemp, bundleName, source, accountId, properties);
  console.info(`Succeeded in setting watermarkImage policy.`);
} catch (err) {
  console.error(`Failed to set watermarkImage policy. Code: ${err.code}, message: ${err.message}`);
}
```

```ts
import { securityManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace with actual values.
let bundleName: string = 'com.example.myapplication';
let source: string = '/data/storage/el1/base/test.png';
let accountId: number = 100;
// Set them with actual values. The device screen size is 1260 × 2720, and the watermark image size is 100 × 100. In this example, the watermark properties are set to 28 rows and 12 columns. Since 28 × 100 > 2720, the grid layout cannot fit within the window. As a result, the watermark will be repeatedly tiled across the entire application window, starting from the top-left corner. Any watermark image that exceeds the right or bottom edges of the window will be clipped.
let properties: securityManager.WatermarkProperties = {
  intervalsRow: 28,
  intervalsCol: 12
};
try {
  securityManager.setWatermarkImage(wantTemp, bundleName, source, accountId, properties);
  console.info(`Succeeded in setting watermarkImage policy.`);
} catch (err) {
  console.error(`Failed to set watermarkImage policy. Code: ${err.code}, message: ${err.message}`);
}
```

## securityManager.getWatermarkImageApps

getWatermarkImageApps(admin: Want, accountId: number): Array\<string\>

Obtains the list of application bundle names for which watermarks have been set for a specified user.

**Since:** 26.0.0

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SECURITY

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name     | Type                                                   | Mandatory| Description          |
| ----------- | ------------------------------------------------------- | ---- | -------------- |
| admin       | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|
| accountId   | number                                                  | Yes  | User ID, which must be greater than or equal to 0. You can call [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1) of **@ohos.account.osAccount** to obtain the user ID.|

**Return value**

| Type  | Description                |
| ------ | -------------------- |
| Array&lt;string&gt; | List of application bundle names for which watermarks have been set.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200012  | Parameter verification failed. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { securityManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace with actual values.
let accountId: number = 100;
try {
  let result: Array<string> = securityManager.getWatermarkImageApps(wantTemp, accountId);
  console.info(`Succeeded in getting watermark image apps, result : ${JSON.stringify(result)}`);
} catch (err) {
  console.error(`Failed to get watermark image apps. Code: ${err.code}, message: ${err.message}`);
}
```


## securityManager.setDeviceSecurityLevelPolicy

setDeviceSecurityLevelPolicy(level: DeviceSecurityLevelPolicy): void

Sets the device security level policy. This API is applicable to the scenario where an enterprise uniformly manages the terminal security baseline, for example, requiring the device to remain at the factory default security level. Before calling this API, you can call [common.isFeatureSupported](./js-apis-enterprise-common.md#commonisfeaturesupported) (with common.ManagedFeature.DEVICE_SECURITY_LEVEL as the input parameter) to check whether the device supports the device security level feature.

> **NOTE**
>
> 1. The device security level is a tiered security mechanism provided on PC/2in1 devices. It is divided into different levels based on the degree of impact on system security. From high to low, the system security levels are DSL0, DSL1, and DSL2.
>
> 2. DSL0: factory default security. The device retains the default security configuration from the factory, with no downgrade of system security capabilities, providing the highest security.
>
> 3. DSL1: reduced security. On the basis of DSL0, some system security controls are moderately relaxed, providing lower security than DSL0.
>
> 4. DSL2: relaxed security. On the basis of DSL1, system security controls are further relaxed, providing the lowest security.
>
> 5. This API is used to set the range of device security levels selectable by users. For the selectable levels corresponding to each policy, see [DeviceSecurityLevelPolicy](#devicesecuritylevelpolicy).

**Since:** 26.0.1

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences:** This API can be called normally on PC/2in1 devices, and returns error code 801 on other devices.

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| level | [DeviceSecurityLevelPolicy](#devicesecuritylevelpolicy) | Yes | Device security level policy. |

**Error Codes**

For details about the following error codes, refer to [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Information |
| -------- | -------- |
| 9200001 | The application is not an administrator application of the device. |
| 9200002 | The administrator application does not have permission to manage the device. |
| 9200012 | Parameter verification failed. |
| 9200016 | Service timeout. |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 801 | Capability not supported. Failed to call the API due to limited device capabilities. |

**Example**

```ts
import { common, securityManager } from '@kit.MDMKit';

// Before calling this API, check whether the device supports the device security level feature.
let isSupported: boolean = common.isFeatureSupported(common.ManagedFeature.DEVICE_SECURITY_LEVEL);
if (isSupported) {
  try {
    securityManager.setDeviceSecurityLevelPolicy(securityManager.DeviceSecurityLevelPolicy.ALLOW_BALANCED);
    console.info('setDeviceSecurityLevelPolicy success');
  } catch (err) {
    console.error('setDeviceSecurityLevelPolicy fail: ' + JSON.stringify(err));
  }
} else {
  console.info('The device security level feature is not supported.');
}
```

## securityManager.getDeviceSecurityLevelPolicy

getDeviceSecurityLevelPolicy(): DeviceSecurityLevelPolicy

Obtains the device security level policy.

> **NOTE**
>
> 1. The device security level policy returned by this API is the range of device security levels that users can select. For the leveling mechanism and the selectable levels corresponding to each policy, see [setDeviceSecurityLevelPolicy](#securitymanagersetdevicesecuritylevelpolicy).
>
> 2. If this policy has not been set on the device, the default value DEFAULT_ENFORCED is returned.

**Since:** 26.0.1

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This API can be used only in the stage model.

**Return value:**

| Type | Description |
| -------- | -------- |
| [DeviceSecurityLevelPolicy](#devicesecuritylevelpolicy) | Device security level policy. |

**Error Codes**

For details about the following error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Information |
| -------- | -------- |
| 9200001 | The application is not an administrator application of the device. |
| 9200002 | The administrator application does not have permission to manage the device. |
| 9200016 | Service timeout. |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { securityManager } from '@kit.MDMKit';

try {
  let policy = securityManager.getDeviceSecurityLevelPolicy();
  console.info('getDeviceSecurityLevelPolicy policy: ' + policy);
} catch (err) {
  console.error('getDeviceSecurityLevelPolicy fail: ' + JSON.stringify(err));
}
```

## securityManager.openSession

openSession(accountId: number): Promise&lt;Uint8Array&gt;

Opens a session for user identity authentication credential changes and obtains a challenge value (used for anti-replay verification in subsequent identity authentication).

> **NOTE**
>
> The system session is unique. If openSession is called multiple times to open sessions, only the last opened session takes effect, and the previous sessions are automatically closed.

**Since:** 26.0.1

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This API can be used only in the stage model.

**Device behavior differences:** This API can be called normally on PC/2-in-1 devices, and returns error code 801 on other devices.

**Parameters**

| Name      | Type                                                    | Mandatory | Description                                                                                     |
| --------- | ------------------------------------------------------- | --------- | ---------------------------------------------------------------------------------------- |
| accountId | number                                                  | Yes       | OS account ID. The value range is greater than or equal to 0.<br/>accountId can be obtained through APIs such as [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9). |

**Return value:**

| Type                   | Description                                   |
| ---------------------- | -------------------------------------- |
| Promise&lt;Uint8Array&gt; | Promise object used to return the challenge value. |

**Error codes:**

For details about the following error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Information                                                                       |
| -------- | ------------------------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device.             |
| 9200002  | The administrator application does not have permission to manage the device.   |
| 9200012  | Parameter verification failed.                                                 |
| 9200016  | Service timeout.                                                               |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**Example:**

```ts
import { securityManager } from '@kit.MDMKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Replace it with the actual account ID.
let accountId: number = 100;
securityManager.openSession(accountId).then((challenge: Uint8Array) => {
  console.info(`Succeeded in opening session, challenge: ${JSON.stringify(challenge)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to open session. Code: ${err.code}, message: ${err.message}`);
});
```

## securityManager.closeSession

closeSession(accountId: number): void

Closes the user identity authentication credential change session.

> **NOTE**
>
> The system session is unique, and only one valid session exists at a time. A session is closed in the following cases:
>
> 1. It is closed by actively calling closeSession.
>
> 2. When openSession is called again, the old session is automatically closed.
>
> 3. The session is automatically closed upon timeout (10 minutes by default).
>
> After the session is closed, both the challenge value and authToken corresponding to the session become invalid and must be obtained again.

**Since:** 26.0.1

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This API can be used only in the stage model.

**Device behavior differences:** This API can be called normally on PC/2-in-1 devices, and returns error code 801 on other devices.

**Parameters**

| Name      | Type                                                    | Mandatory | Description                                                                                     |
| --------- | ------------------------------------------------------- | --------- | ---------------------------------------------------------------------------------------- |
| accountId | number                                                  | Yes       | Operating system account ID. The value ranges from 0 to a larger integer.<br/>The accountId can be obtained through APIs such as [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9). |

**Error codes**

For details about the following error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Information                                                                       |
| ------------- | ------------------------------------------------------------------------------ |
| 9200001       | The application is not an administrator application of the device.             |
| 9200002       | The administrator application does not have permission to manage the device.   |
| 9200012       | Parameter verification failed.                                                 |
| 9200016       | Service timeout.                                                               |
| 201           | Permission verification failed. The application does not have the permission required to call the API. |
| 801           | Capability not supported. Failed to call the API due to limited device capabilities. |

**Example**

```ts
import { securityManager } from '@kit.MDMKit';

let accountId: number = 100;
try {
  securityManager.closeSession(accountId);
  console.info('Succeeded in closing session.');
} catch(err) {
  console.error(`Failed to close session. Code: ${err.code}, message: ${err.message}`);
}
```

## securityManager.addUserExtendCredential

addUserExtendCredential(info: AddCredentialInfo, accountId: number): Promise&lt;Uint8Array&gt;

Adds a third-party custom identity authentication credential for the specified account, passes in the authentication plug-in information and the authentication token (optional), and obtains the credential ID. This API uses a promise to return the result.

**Since:** 26.0.1

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This API can be used only in the stage model.

**Device behavior differences:** This API can be called normally on PC/2-in-1 devices, and returns error code 801 on other devices.

**Parameters**

| Name      | Type                                                    | Mandatory | Description                                                                                     |
| --------- | ------------------------------------------------------- | --------- | ------------------------------------------------------------------------------------------------ |
| info      | [AddCredentialInfo](#addcredentialinfo)                 | Yes       | Indicates the information about the credential to add.                                           |
| accountId | number                                                  | Yes       | OS account ID. The value ranges from 0 to a larger value.<br/>accountId can be obtained through APIs such as [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9). |

**Return value**

| Type                   | Description                                   |
| ---------------------- | -------------------------------------- |
| Promise&lt;Uint8Array&gt; | Promise object that returns the credential ID. |

**Error codes**

For details about the following error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Information                                                                       |
| -------- | ------------------------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device.             |
| 9200002  | The administrator application does not have permission to manage the device.   |
| 9200012  | Parameter verification failed.                                                 |
| 9200016  | Service timeout.                                                               |
| 9201052  | USB key session time out.                                                |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**Example**

```ts
import { securityManager } from '@kit.MDMKit';
import { BusinessError } from '@kit.BasicServicesKit';

let accountId: number = 100;
let info: securityManager.AddCredentialInfo = {
  pluginInfo: 'com.example.ukey_plugin'
};
securityManager.addUserExtendCredential(info, accountId).then((credentialId: Uint8Array) => {
  console.info(`Succeeded in adding credential, credentialId: ${JSON.stringify(credentialId)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to add credential. Code: ${err.code}, message: ${err.message}`);
});
```

## securityManager.removeUserExtendCredential

removeUserExtendCredential(info: RemoveCredentialInfo, accountId: number): void

Removes a third-party custom identity authentication credential based on the credential ID. Pass in the credential ID and the authentication token (optional).

**Since:** 26.0.1

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This API can be used only in the stage model.

**Device behavior differences:** This API can be called normally on PC/2-in-1 devices, and returns error code 801 on other devices.

**Parameters**

| Name    | Type                                                    | Mandatory | Description                                                                                     |
| --------- | ------------------------------------------------------- | ---- | ---------------------------------------------------------------------------------------- |
| info   | [RemoveCredentialInfo](#removecredentialinfo)           | Yes   | Information about the credential to be removed.                                                                     |
| accountId | number                                                  | Yes   | Operating system account ID. Value range: greater than or equal to 0.<br/>accountId can be obtained through APIs such as [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9). |

**Error Codes**

For details about the following error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Information                                                               |
| ------------- | ------------------------------------------------------------------------------- |
| 9200001       | The application is not an administrator application of the device.              |
| 9200002       | The administrator application does not have permission to manage the device.    |
| 9200012       | Parameter verification failed.                                                  |
| 9200016       | Service timeout.                                                                |
| 9201052       | USB key session time out.                                                       |
| 201           | Permission verification failed. The application does not have the permission required to call the API. |
| 801           | Capability not supported. Failed to call the API due to limited device capabilities. |

**Example**

```ts
import { securityManager } from '@kit.MDMKit';

let accountId: number = 100;
let credentialId: Uint8Array = new Uint8Array([1, 2, 3, 4]);
let info: securityManager.RemoveCredentialInfo = {
  credentialId: credentialId
};
try {
  securityManager.removeUserExtendCredential(info, accountId);
  console.info('Succeeded in removing credential.');
} catch(err) {
  console.error(`Failed to remove credential. Code: ${err.code}, message: ${err.message}`);
}
```

## securityManager.getUserExtendCredential

getUserExtendCredential(accountId: number): Promise&lt;UserExtCredentialInfo[]&gt;

Obtains the third-party custom identity authentication credential information of the specified account. This API uses a promise to return the result asynchronously.

**Since:** 26.0.1

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This API can be used only in the stage model.

**Parameters:**

| Name      | Type                                                    | Mandatory | Description                                                                                     |
| --------- | ------------------------------------------------------- | --------- | ---------------------------------------------------------------------------------------------- |
| accountId | number                                                  | Yes       | Operating system account ID. The value range is greater than or equal to 0.<br/>The accountId can be obtained through APIs such as [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9). |

**Return value:**

| Type                              | Description                                       |
| --------------------------------- | ------------------------------------------ |
| Promise&lt;[UserExtCredentialInfo](#userextcredentialinfo)[]&gt; | Promise used to return the list of third-party custom identity authentication credential information. |

**Error codes:**

For details about the following error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Information                                                                       |
| -------- | ------------------------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device.             |
| 9200002  | The administrator application does not have permission to manage the device.   |
| 9200012  | Parameter verification failed.                                                 |
| 9200016  | Service timeout.                                                               |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example:**

```ts
import { securityManager } from '@kit.MDMKit';
import { BusinessError } from '@kit.BasicServicesKit';

let accountId: number = 100;
securityManager.getUserExtendCredential(accountId).then((credentials: securityManager.UserExtCredentialInfo[]) => {
  console.info(`Succeeded in getting credentials: ${JSON.stringify(credentials)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get credentials. Code: ${err.code}, message: ${err.message}`);
});
```

## securityManager.setUnlockPolicy

setUnlockPolicy(policy: UnlockPolicy, accountId: number): void

Sets the device unlock policy for the specified account.

**Since:** 26.0.1

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This API can be used only in the stage model.

**Device behavior differences:** This API can be called normally on PC/2in1 devices, and returns error code 801 on other devices.

**Parameters**

| Name    | Type                                                    | Mandatory | Description                                                                                     |
| ------- | ------------------------------------------------------- | --------- | ---------------------------------------------------------------------------------------------- |
| policy    | [UnlockPolicy](#unlockpolicy)                           | Yes   | Device unlock policy.                                                                       |
| accountId | number                                                  | Yes   | Operating system account ID. The value must be greater than or equal to 0.<br/>accountId can be obtained through APIs such as [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9). |

**Error codes**

For details about the following error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Information                                                              |
| ------------- | ------------------------------------------------------------------------------ |
| 9200001       | The application is not an administrator application of the device.             |
| 9200002       | The administrator application does not have permission to manage the device.   |
| 9200012       | Parameter verification failed.                                                 |
| 9200016       | Service timeout.                                                               |
| 201           | Permission verification failed. The application does not have the permission required to call the API. |
| 801           | Capability not supported. Failed to call the API due to limited device capabilities. |

**Example**

```ts
import { securityManager } from '@kit.MDMKit';

let accountId: number = 100;
try {
  securityManager.setUnlockPolicy(securityManager.UnlockPolicy.EXTENDED_AUTH_REQUIRED, accountId);
  console.info('Succeeded in setting unlock policy.');
} catch(err) {
  console.error(`Failed to set unlock policy. Code: ${err.code}, message: ${err.message}`);
}
```

## securityManager.getUnlockPolicy

getUnlockPolicy(accountId: number): UnlockPolicy

Obtains the device unlock policy of the specified account.

**Since:** 26.0.1

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This API can be used only in the stage model.

**Device behavior differences:** This API can be called normally on PC/2-in-1 devices, and returns error code 801 on other devices.

**Parameters**

| Name    | Type                                                    | Mandatory | Description                                                                                     |
| ------- | ------------------------------------------------------- | --------- | ---------------------------------------------------------------------------------------------- |
| accountId | number                                                  | Yes       | OS account ID. The value ranges from 0 to the maximum value.<br/>The accountId can be obtained through APIs such as [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9). |

**Return value:**

| Type                          | Description               |
| ----------------------------- | ------------------------- |
| [UnlockPolicy](#unlockpolicy) | Device unlock policy. |

**Error codes:**

For details about the following error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Information                                                                       |
| -------- | ------------------------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device.             |
| 9200002  | The administrator application does not have permission to manage the device.   |
| 9200012  | Parameter verification failed.                                                 |
| 9200016  | Service timeout.                                                               |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**Example**

```ts
import { securityManager } from '@kit.MDMKit';

let accountId: number = 100;
try {
  let policy = securityManager.getUnlockPolicy(accountId);
  console.info(`Succeeded in getting unlock policy: ${policy}`);
} catch(err) {
  console.error(`Failed to get unlock policy. Code: ${err.code}, message: ${err.message}`);
}
```

## securityManager.setWeakPinEnable
 
setWeakPinEnable(isEnable: boolean, fd?: number): void
 
Sets the weak password library for lock screen weak password verification. After the weak password library is set, when a user sets a lock screen password, the system verifies the password against the weak password list in the weak password library. If the password exists in the weak password list, the system rejects the password to prevent the user from setting an overly simple password. This is applicable to enterprise security compliance scenarios, such as preventing employees from using common weak passwords (for example, 123456 and 000000), thereby improving device security protection. After the weak password library is canceled, weak password verification is no longer performed when a user sets a lock screen password. Weak password verification supplements the existing password verification logic and does not replace the existing verification rules (such as password length and complexity). Setting or canceling the weak password library does not affect the existing password verification logic.
 
**Since:** 26.0.1
 
**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SECURITY
 
**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
 
**Model restriction:** This API can be used only in the stage model.
 
**Parameters**
 
| Name     | Type    | Mandatory | Description                                                         |
| -------- | ------- | ---- | ------------------------------------------------------------ |
| isEnable | boolean | Yes  | Whether to set the weak password library. The value **true** means to set it, and **false** means to cancel it.            |
| fd       | number  | No   | File descriptor of the weak password library file. This parameter is mandatory when setting the weak password library and is ignored when canceling it.<br>The weak password library file must be placed in a path that the application has permission to access, such as the application sandbox path (for the correspondence between the application sandbox path and the real path, see [Correspondence Between Application Sandbox Path and Real Physical Path](../../file-management/app-sandbox-directory.md#mappings-between-application-sandbox-paths-and-physical-paths)).<br>Each line in the file corresponds to one weak password.<br>The file size cannot exceed 16 MB. |
 
**Error codes**
 
For details about the following error codes, refer to [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).
 
| ID | Error Information                                            |
| ------------- | ------------------------------------------------------------ |
| 201           | Permission verification failed. The application does not have the permission required to call the API. |
| 9200001       | The application is not an administrator application of the device. |
| 9200002       | The administrator application does not have permission to manage the device. |
| 9200012       | Parameter verification failed. |
| 9200016       | Service timeout. |
 
**Example**

Example of a weak password library file (weak_pin.txt), with one weak password per line:

```txt
123456
000000
111111
888888
666666
```

**Example**

```ts
import { securityManager } from '@kit.MDMKit';
import { fileIo } from '@kit.CoreFileKit';
 
// Replace it based on the actual situation. The weak password file must be placed in the application sandbox directory.
// Weak password file format: each line corresponds to a weak password, such as 123456, 000000, etc.
const filePath = '/data/storage/el1/base/weak_pin.txt';
let fd: number = fileIo.openSync(filePath, fileIo.OpenMode.READ_ONLY).fd;
try {
  securityManager.setWeakPinEnable(true, fd);
  console.info(`Succeeded in setting weak pin enable.`);
} catch (err) {
  console.error(`Failed to set weak pin enable. Code: ${err.code}, message: ${err.message}`);
} finally {
  fileIo.closeSync(fd);
}
```
 
## securityManager.isWeakPinEnabled
 
isWeakPinEnabled(): boolean
 
Queries whether the lock screen weak password library has been set. Enterprises can query the current status of the weak password library through this API for policy auditing and compliance checking.
 
**Since:** 26.0.1
 
**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SECURITY
 
**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
 
**Model restriction:** This API can be used only in the Stage model.
 
**Return value:**
 
| Type    | Description                                                         |
| ------- | ------------------------------------------------------------ |
| boolean | true indicates that the weak password library has been set, and false indicates that it has not been set.              |
 
**Error Codes:**
 
For details about the following error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).
 
| ID | Error Information                                            |
| ------------- | ------------------------------------------------------------ |
| 201           | Permission verification failed. The application does not have the permission required to call the API. |
| 9200001       | The application is not an administrator application of the device. |
| 9200002       | The administrator application does not have permission to manage the device. |
| 9200016       | Service timeout. |
 
**Example**
 
```ts
import { securityManager } from '@kit.MDMKit';
 
try {
  let result: boolean = securityManager.isWeakPinEnabled();
  console.info(`Succeeded in checking weak pin enabled, result: ${result}`);
} catch (err) {
  console.error(`Failed to check weak pin enabled. Code: ${err.code}, message: ${err.message}`);
}
```

## securityManager.getPasswordLastChangedTime

getPasswordLastChangedTime(accountId: number): number

Obtains the time when the user last changed the lock screen password based on the system account ID, and returns it synchronously. The account ID refers to the system account ID (100 for the primary user, and incremented sequentially for sub-users), not a third-party application account. The password refers to the device lock screen password (passcode), excluding other authentication credentials such as fingerprints and face recognition. Enterprises can query the time when the password was last changed through this API for password policy auditing and compliance checks.

**Since:** 26.1.0

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SECURITY

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name      | Type   | Mandatory | Description                                                         |
| --------- | ------ | --------- | ------------------------------------------------------------ |
| accountId | number | Yes       | User ID, which specifies a specific user. The value range is greater than or equal to 0. The accountId can be obtained through APIs such as [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1) in @ohos.account.osAccount. |

**Return value**

| Type | Description |
| ------ | ---------------------------------- |
| number | Timestamp of the last password change, in milliseconds (ms). The return value is a Unix timestamp (the number of milliseconds elapsed since 1970-01-01 00:00:00 UTC), and the application needs to convert it to local time based on the time zone settings. If the user has never set a lock screen password or has disabled the lock screen password, the API returns error code 9200016. |

**Error codes**

For details about the following error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Information |
| -------- | ------------------------------------------------------------ |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200006  | The specified account ID is invalid. |
| 9200016  | Service timeout. |

**Example**

```ts
import { securityManager } from '@kit.MDMKit';

// Replace it based on the actual situation.
let accountId: number = 100;
try {
  let result: number = securityManager.getPasswordLastChangedTime(accountId);
  console.info(`Succeeded in getting password last changed time, result: ${result}`);
  // result is a Unix timestamp (in milliseconds). Convert it to local time based on the time zone settings.
  // For example, if the password was changed one hour ago and the current UTC time is 2026-08-27 16:01:36, the return value is 1787842896000, indicating UTC time 2026-08-27 15:01:36.
  let date: Date = new Date(result);
  console.info(`Password last changed time: ${date.toLocaleString()}`);
} catch (err) {
  console.error(`Failed to get password last changed time. Code: ${err.code}, message: ${err.message}`);
}
```

## CertBlob

Represents the certificate information.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This API can only be used in the stage model.

| Name  | Type      | Read-Only| Optional| Description              |
| ------ | ---------- | ---- | ---- | ------------------ |
| inData | Uint8Array | No  | No|Binary content of the certificate.|
| alias  | string     | No  | No|Certificate alias. The value length must be less than 40 characters.        |

## PasswordPolicy

Represents a device screen lock password policy.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This API can only be used in the stage model.

| Name        | Type    | Read-Only| Optional| Description                           |
| ----------- | --------| ---- | ---- | --------------------------- |
| complexityRegex | string | No| Yes| Regular expression for password complexity.|
| validityPeriod | number | No| Yes| Password validity period, in ms.|
| additionalDescription | string | No| Yes| Password complexity description, for example, "The password must contain 8 to 30 characters consisting of letters, digits, and special characters".|
| passwordAlgs | [PasswordAlgs](#passwordalgs) | No| Yes| Encryption algorithm used to process password data. After the setting, the encryption algorithm specified by this parameter is used to process the original password into a password credential on a PC/2-in-1 device. This parameter has no effect on other device types.<br>**Since:** 26.0.0<br>**Model restriction**: This API can be used only in the stage model.|

## ClipboardPolicy

Represents a device clipboard policy.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This API can only be used in the stage model.

| Name        | Value| Description                           |
| ----------- | -------- | ------------------------------- |
| DEFAULT | 0  | Default policy, which indicates no policy.|
| IN_APP | 1  | Allow the clipboard to be used in the same application.|
| LOCAL_DEVICE | 2  | Allow the clipboard to be used on the same device.|
| CROSS_DEVICE | 3  | Allow the clipboard to be used across devices.|

## ApplicationInstance<sup>20+</sup>

Application instance

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

| Name        | Type    | Read-Only| Optional| Description                           |
| ----------- | --------| ---- | ---- | --------------------------- |
| appIdentifier | string | No| No| The [unique identifier](../apis-ability-kit/js-apis-bundleManager-bundleInfo.md#signatureinfo) of an application. If an application does not have **appIdentifier**, **appId** can be used instead. Both **bundleInfo.signatureInfo.appIdentifier** and **bundleInfo.signatureInfo.appId** can be obtained via the [bundleManager.getBundleInfo](../apis-ability-kit/js-apis-bundleManager.md#bundlemanagergetbundleinfo14-2) API.|
| accountId  | number     | No| No| User ID, which must be greater than or equal to 0. You can call [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1) of **@ohos.account.osAccount** to obtain the user ID.        |
| appIndex  | number     | No| No| Index of the application clone. The default value is **0**.<br> If **appIndex** is set to **0**, the main application is used. If **appIndex** is set to a value greater than 0, the application clone with the specified index is used.       |

## PermissionManagedState<sup>20+</sup>

Represents the management status of application permissions.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

| Name        | Value| Description                           |
| ----------- | -------- | ------------------------------- |
| DEFAULT | 1  | The permission is granted by the user by default.|
| GRANTED | 0  | This permission is granted silently.|
| DENIED | -1  | This permission is denied silently.|

## WatermarkProperties

Defines watermark properties.

**Since:** 26.0.0

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

| Name        | Type    | Read-Only| Optional|  Description                      |
| ----------- | --------| ---- | ----| ---------------------------- |
| intervalsRow | number | No  | No| Number of rows for displaying the watermark.|
| intervalsCol | number | No  | No| Number of columns for displaying the watermark.|

## PasswordAlgs

Enumerates the encryption algorithms used to process password data.

**Since:** 26.0.0

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

| Name        | Value| Description                           |
| ----------- | -------- | ------------------------------- |
| SCRYPT_HKDF_AES | 0  | SCRYPT-HKDF-AES combined encryption algorithm.|
| SCRYPT_HKDF_SM4 | 1  | SCRYPT-HKDF-SM4 combined encryption algorithm.|

## DeviceSecurityLevelPolicy

Enumerates the device security level policies.

**Since:** 26.0.1

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This API can be used only in the stage model.

| Name | Value | Description |
| -------- | -------- | -------- |
| DEFAULT_ENFORCED | 0 | Only the factory default security level (DSL0) can be selected. |
| ALLOW_BALANCED | 1 | The factory default security level (DSL0) and the reduced security level (DSL1) can be selected. |
| ALLOW_FLEXIBLE | 2 | The factory default security level (DSL0), the reduced security level (DSL1), and the flexible security level (DSL2) can be selected. |

## AddCredentialInfo

Defines the information for adding a credential.

**Since:** 26.0.1

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This API can be used only in the stage model.

| Name       | Type       | Read-only | Optional | Description               |
| ---------- | ---------- | ---- | ---- | ------------------ |
| pluginInfo | string     | No   | No   | Indicates the authentication plug-in information. |
| authToken  | Uint8Array | No   | Yes   | Indicates the authentication token.     |

## RemoveCredentialInfo

Defines the information for removing a credential.

**Since:** 26.0.1

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This API can be used only in the stage model.

| Name         | Type       | Readable | Optional | Description                        |
| ------------ | ---------- | -------- | -------- | ---------------------------------- |
| credentialId | Uint8Array | No       | No       | Indicates the credential ID.       |
| authToken    | Uint8Array | No       | Yes      | Indicates the authentication token. |

## UserExtCredentialInfo

Represents the information about a third-party custom identity authentication credential.

**Since:** 26.0.1

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This API can be used only in the stage model.

| Name         | Type       | Read-only | Optional | Description                          |
| ------------ | ---------- | --------- | -------- | ------------------------------------ |
| credentialId | Uint8Array | No        | No       | Indicates the credential ID.         |
| pluginInfo   | string     | No        | No       | Indicates the authentication plug-in information. |

## UnlockPolicy

Represents the device unlock policy.

**Since:** 26.0.1

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction:** This API can be used only in the stage model.

| Name                  | Value | Description                                       |
| --------------------- | -- | ------------------------------------------ |
| DEFAULT               | 0  | The device is unlocked using only the built-in system authentication method, that is, the built-in lock screen authentication method.                         |
| EXTENDED_AUTH_ONLY    | 1  | The device is unlocked using only third-party custom authentication. When the device is unlocked, identity verification is performed only through the third-party custom authentication method, without requiring the system lock screen password.                       |
| EXTENDED_AUTH_REQUIRED | 2  | The device is unlocked using a combination of third-party custom authentication and built-in system authentication. When the device is unlocked, identity verification must pass both the third-party custom authentication method and the system lock screen password.           |