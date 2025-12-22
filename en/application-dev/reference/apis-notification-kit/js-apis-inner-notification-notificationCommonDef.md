# NotificationCommonDef
<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @michael_woo888-->
<!--Designer: @dongqingran; @wulong158-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->

Describes the bundle information of an application.

> **NOTE**
>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## BundleOption

Describes the **BundleOption** information, that is, the bundle information of an application.

**System capability**: SystemCapability.Notification.Notification

| Name  | Type  | Read Only| Optional| Description  |
| ------ | ------ | ----| -- |  ------ |
| bundle | string | No | No| Application name.|
| uid    | number | No | Yes| UID of an application, which is obtained from [ApplicationInfo](../apis-ability-kit/js-apis-bundleManager-applicationInfo.md). The default value is **0**. This parameter is mandatory for telematics devices.|

## GrantedBundleInfo<sup>22+</sup> 

Describes the authorized bundle information.

**System capability**: SystemCapability.Notification.Notification

| Name  | Type  | Read Only| Optional| Description  |
| ------ | ------ | ----| -- |  ------ |
| bundleName | string | No | No| Bundle name of the application.|
| appName    | string | Yes | Yes| Application name, which is obtained from the **label** of [ApplicationInfo](../apis-ability-kit/js-apis-bundleManager-applicationInfo.md).|
| appIndex   | int | Yes | No| Index of an application clone, which takes effect only for application clones. The value is obtained from the **appIndex** of [ApplicationInfo](../apis-ability-kit/js-apis-bundleManager-applicationInfo.md).|
