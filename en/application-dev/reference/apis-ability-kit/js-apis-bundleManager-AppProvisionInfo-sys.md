# AppProvisionInfo (System API)
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @kongjing2-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=237dbe5ba2f3350597af7253327d6cd79caefee3 translatedAt=2026-11-25T11:23:46.265Z pushedAt=2026-11-26T02:51:21.403Z nl=1 -->

The module provides information in the [HarmonyAppProvision configuration file](../../security/app-provision-structure.md). The information can be obtained through [getAppProvisionInfo](./js-apis-bundleManager-sys.md#bundlemanagergetappprovisioninfo10).

> **NOTE**
>
> The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs provided by this module are system APIs.

## Modules to Import

```ts
import { bundleManager } from '@kit.AbilityKit';
```

## AppProvisionInfo

**System capability**: SystemCapability.BundleManager.BundleFramework.Core

**System API**: This is a system API.

| Name                     | Type  | Read-Only| Optional| Description                |
| ------------------------- | ------ | ---- | ---- | -------------------- |
| versionCode              | number | Yes  | No  | Version number of the configuration file.|
| versionName              | string | Yes  | No  | Version name of the configuration file. |
| uuid                     | string | Yes  | No  | UUID in the configuration file.|
| type                     | string | Yes  | No  | Type of the configuration file, which can be **debug** or **release**.|
| appDistributionType      | string | Yes  | No  | [Distribution type](../../security/app-provision-structure.md) in the configuration file.|
| validity                 | [Validity](#validity) | Yes  | No  | Validity period in the configuration file.|
| developerId              | string | Yes  | No  | Developer ID in the configuration file.|
| certificate              | string | Yes  | No  | Certificate information in the configuration file.|
| apl                      | string | Yes  | No  | APL in the configuration file, which can be **normal**, **system_basic**, or **system_core**.|
| issuer                      | string | Yes  | No  | Issuer name in the configuration file.|
|appIdentifier<sup>11+</sup>| string         | Yes  | No  | Unique ID of the application. For details, see [What Is appIdentifier](../../quick-start/common-problem-of-application.md#what-is-appidentifier).  |
| organization<sup>12+</sup> | string | Yes  | No  | Organization of the application.|
| bundleName<sup>23+</sup> | string | Yes  | Yes  | Bundle name of the application.|
| appServiceCapabilities | string | Yes   | Yes   | Service capability of the application.<br/>**Since:** 26.0.1 <br/>**Model restriction:** This API can be used only in the stage model. |
| appIndex | number | Yes   | Yes   | Clone index of the application.<br/>**Since:** 26.0.1 <br/>**Model restriction:** This API can be used only in the stage model.|
| specifiedDistributionType | string | Yes   | Yes   | Distribution type of the application.<br/>**Since:** 26.0.1 <br/>**Model restriction:** This API can be used only in the stage model. |
| additionalInfo | string | Yes   | Yes   | Additional information of the application.<br/>**Since:** 26.0.1 <br/>**Model restriction:** This API can be used only in the stage model. |

## Validity

**System capability**: SystemCapability.BundleManager.BundleFramework.Core

**System API**: This is a system API.

| Name                     | Type  | Read-Only| Optional| Description                |
| ------------------------- | ------ | ---- | ---- | -------------------- |
| notBefore                 | number | Yes   | No   | Indicates the start time of the validity period of the configuration file, in s. |
| notAfter                  | number | Yes   | No   | Indicates the end time of the validity period of the configuration file, in s. |