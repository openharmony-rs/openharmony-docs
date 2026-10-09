# NotificationCommonDef
<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @wangsen1994-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=1ded46b3f2c6157598c112b16f192beb1f37cf1d translatedAt=2026-10-08T02:17:13.795Z pushedAt=2026-10-08T09:16:44.966Z -->

The **NotificationCommonDef** module defines the common data structures used in notification-related APIs.

> **NOTE**
>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## BundleOption

Describes the **BundleOption** information, that is, the bundle information of an application.

**System capability**: SystemCapability.Notification.Notification

| Name  | Type  | Read Only| Optional| Description  |
| ------ | ------ | ----| -- |  ------ |
| bundle | string | No  | No | Bundle name of the application. The string length cannot exceed 202 bytes, and the excess part will be truncated. |
| uid    | number | No  | Yes | UID of the application, which is obtained from [ApplicationInfo](../apis-ability-kit/js-apis-bundleManager-applicationInfo.md#applicationinfo-1). The default value is **0**. This parameter is mandatory in application clone<!--Del--> or telematics device<!--DelEnd--> scenarios.|

## GrantedBundleInfo<sup>22+</sup>

Describes the authorized bundle information.

**System capability**: SystemCapability.Notification.Notification

| Name  | Type  | Read Only| Optional| Description  |
| ------ | ------ | ----| -- |  ------ |
| bundleName | string | No | No | Bundle name of the application. |
| appIndex   | number | Yes | No | Index of an application clone, which takes effect only for application clones. The value is obtained from the **appIndex** of [ApplicationInfo](../apis-ability-kit/js-apis-bundleManager-applicationInfo.md#applicationinfo-1). |
| appName    | string | Yes | Yes | Application name, which is obtained from the **label** of [ApplicationInfo](../apis-ability-kit/js-apis-bundleManager-applicationInfo.md#applicationinfo-1). |

## UserGrantSetting

Describes the user authorization settings.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Notification.Notification

| Name  | Type  | Read Only| Optional| Description  |
| ------ | ------ | ----| -- |  ------ |
| userGrantEnabled | boolean | Yes | No| Whether the **Allow access to notifications on this device** switch is toggled on. true: **yes**; false: **no**.|
| grantedBundleInfos    | Array\<[GrantedBundleInfo](#grantedbundleinfo22)\> | Yes | Yes| List of apps for which the **Allow access to notifications on this device** switch is toggled on.|
