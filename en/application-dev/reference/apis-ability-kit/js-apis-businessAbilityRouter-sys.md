# @ohos.app.businessAbilityRouter (Service Routing Module) (System API)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zhu-feimo-->
<!--Designer: @ccllee1-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

The module provides APIs for you to query the information about routable ability components within applications installed on the device. It offers a standardized framework for managing and accessing service capabilities. It allows you to register your application's functionalities as standardized services under specific categories, effectively creating a rich ecosystem or marketplace of capabilities. System applications can leverage this router to easily discover and integrate these predefined ability components. Furthermore, the router enforces unified control over navigation between applications and services. This ensures proper redirection, prevents unauthorized jumps between foreground/background states, and blocks attempts by third-party application to use redirection for unintended distribution, ultimately enhancing system security and user experience.

> **NOTE**
>
> The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
>The APIs provided by this module are system APIs.

## Modules to Import

``` ts
import businessAbilityRouter from '@ohos.app.businessAbilityRouter';
```

## Required Permissions

| Permission                                      | APL    | Description                |
| ------------------------------------------ | ------------ | -------------------- |
| ohos.permission.GET_BUNDLE_INFO_PRIVILEGED | system_basic | Permission to query information about all bundles.|

For details about the APL, see [Basic Concepts in the Permission Mechanism](../../security/AccessToken/app-permission-mgmt-overview.md#basic-concepts-in-the-permission-mechanism).

## BusinessType

Enumerates the types of ability components.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

| Name       | Value  | Description                                |
| ----------- | ---- | ------------------------------------ |
| SHARE       | 0    | Ability of the share type.|
| UNSPECIFIED | 255  | Ability of an unspecified type.  |

## BusinessAbilityFilter

Describes the criteria for filtering ability components.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

| Name        | Type        | Read-only| Optional| Description                                  |
| ------------ | ------------ | ---- | ---- | -------------------------------------- |
| businessType | [BusinessType](#businesstype) | No  | No  | Type of the ability.          |
| mimeType     | string       | No  | Yes  | MIME type supported by the ability.|
| uri          | string       | No  | Yes  | URI supported by the ability.       |

## businessAbilityRouter.queryBusinessAbilityInfo

queryBusinessAbilityInfo(filter: BusinessAbilityFilter, callback: AsyncCallback\<Array\<BusinessAbilityInfo\>\>): void;

Obtains the ability information based on the specified filter criteria. This API uses an asynchronous callback to return the result. If the operation is successful, the ability information is returned; otherwise, an error object is returned.

**Required permissions**: ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name      | Type    | Mandatory  | Description                                   |
| ----------- | ------ | ---- | --------------------------------------- |
| filter | [BusinessAbilityFilter](#businessabilityfilter) | Yes   | Object used to filter the ability information.|
| callback | AsyncCallback\<Array\<[BusinessAbilityInfo](js-apis-bundleManager-businessAbilityInfo-sys.md#businessabilityinfo)\>\> | Yes| Callback used to return the result. If the operation is successful, the ability information that meets the filter criteria is returned; otherwise, an error object is returned.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not System App. Interface caller is not a system app. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. 3. Parameter verification failed. |

**Example**

```ts
import businessAbilityRouter from '@ohos.app.businessAbilityRouter';
import { BusinessError } from '@ohos.base';

let filter: businessAbilityRouter.BusinessAbilityFilter = {businessType: businessAbilityRouter.BusinessType.SHARE};

try {
    businessAbilityRouter.queryBusinessAbilityInfo(filter, (error, data) => {
        if (error) {
            console.error('queryBusinessAbilityInfo failed ' + error.message);
            return;
        }
        console.info('queryBusinessAbilityInfo success');
    });
} catch (error) {
    let message = (error as BusinessError).message;
    console.error('queryBusinessAbilityInfo failed ' + message);
}
```

## businessAbilityRouter.queryBusinessAbilityInfo

queryBusinessAbilityInfo(filter: BusinessAbilityFilter): Promise\<Array\<BusinessAbilityInfo\>\>;

Obtains the ability information based on the specified filter criteria. This API uses a promise to return the result. If the operation is successful, the ability information is returned; otherwise, an error object is returned.

**Required permissions**: ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name      | Type                             | Mandatory  | Description                                   |
| ----------- | ------------------------------- | ---- | --------------------------------------- |
| filter | [BusinessAbilityFilter](#businessabilityfilter) | Yes   | Object used to filter the ability information. |

**Return value**

| Type                                                        | Description                                       |
| ------------------------------------------------------------ | ------------------------------------------- |
| Promise\<Array\<[BusinessAbilityInfo](js-apis-bundleManager-businessAbilityInfo-sys.md#businessabilityinfo)\>\> | Promise used to return the ability information that meets the filter criteria.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not System App. Interface caller is not a system app. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. 3. Parameter verification failed. |

**Example**

```ts
import businessAbilityRouter from '@ohos.app.businessAbilityRouter';
import { BusinessError } from '@ohos.base';

let filter: businessAbilityRouter.BusinessAbilityFilter = {businessType: businessAbilityRouter.BusinessType.SHARE};

try {
    businessAbilityRouter.queryBusinessAbilityInfo(filter)
        .then(() => {
            console.info('queryBusinessAbilityInfo success');
        }).catch((error: BusinessError) => {
            console.error('queryBusinessAbilityInfo failed ' + error.message);
        });
} catch (error) {
    let message = (error as BusinessError).message;
    console.error('queryBusinessAbilityInfo failed ' + message);
}
```
