# @ohos.enterprise.common (Common Module)
<!--Kit: MDM Kit-->
<!--Subsystem: Customization-->
<!--Owner: @huanleima-->
<!--Designer: @liuzuming-->
<!--Tester: @lpw_work-->
<!--Adviser: @zhang_yixin13-->

The module provides pure type definitions for common capabilities within MDM Kit, including enum types and data structs. It exports type declarations only and does not include any implementation logic or executable code.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 22. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { common } from '@kit.MDMKit';
```

## ManagedPolicy

Enumerates enterprise device management policies.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

| Name        | Value| Description                           |
| ----------- | -------- | ------------------------------- |
| DEFAULT | 0  | Default policy with no restrictions applied.|
| DISALLOW | 1  | Policy that disallows extensions from external sources to run.|
| FORCE_OPEN | 2  | Policy that forcibly enables extensions from external sources to run.|

## ApplicationInstance

Defines application instance data.
It is used as an input parameter in the [addUserNonStopApps](./js-apis-enterprise-applicationManager.md#applicationmanageraddusernonstopapps22), [removeUserNonStopApps](./js-apis-enterprise-applicationManager.md#applicationmanagerremoveusernonstopapps22), [addFreezeExemptedApps](./js-apis-enterprise-applicationManager.md#applicationmanageraddfreezeexemptedapps22), and [removeFreezeExemptedApps](./js-apis-enterprise-applicationManager.md#applicationmanagerremovefreezeexemptedapps22) APIs.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

| Name         | Type                            | Read-Only| Optional| Description                                                       |
| ------------- | --------------------------------| ---- | -----| ------------------------------------------------------ |
| appIdentifier          | string       | No  | No| [Unique identifier](../apis-ability-kit/js-apis-bundleManager-bundleInfo.md#signatureinfo) of an application. You can call the [bundleManager.getBundleInfo](../apis-ability-kit/js-apis-bundleManager.md#bundlemanagergetbundleinfo14-2) API to obtain **bundleInfo.signatureInfo.appIdentifier**.          |
| accountId        | number       | No  | No| Account ID. The value is an integer greater than or equal to 0.<br> You can obtain the account ID by calling the [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1) API.           |
| appIndex        | number       | No  | No| Index of the application clone. The value is an integer greater than or equal to 0.<br> You can obtain the index by calling the [getAppCloneIdentity](../apis-ability-kit/js-apis-bundleManager.md#bundlemanagergetappcloneidentity14) API.          |

## InstallationResult

An object that holds the application installation result.
This object is used as a callback parameter in [EnterpriseAdminExtensionAbility.onMarketAppInstallResult](./js-apis-EnterpriseAdminExtensionAbility.md#enterpriseadminextensionabilityonmarketappinstallresult22).

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

| Name         | Type                            | Read-Only| Optional| Description                                                       |
| ------------- | --------------------------------| ---- | -----| ------------------------------------------------------ |
| result        | [Result](#result)       | No  | No| Application installation result.           |
| message        | string       | No  | No| Application installation result message.          |

## Result

Enumerates application installation results.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

| Name        | Value| Description                           |
| ----------- | -------- | ------------------------------- |
| SUCCESS | 0  | The application is installed successfully.|
| FAIL | -1  | The application fails to be installed.|
