# ElementName
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @memghaiyang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=1bd317f06f1afd85920306c4a4cf71333749080f translatedAt=2026-09-03T11:05:21.625Z pushedAt=2026-09-05T10:47:30.526Z -->

ElementName information, which can be obtained through [Context.getElementName](js-apis-inner-app-context.md#contextgetelementname7).

> **NOTE**
> 
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> Since API version 9, this module is no longer maintained. You are advised to use [bundleManager-ElementName](js-apis-bundleManager-elementName.md) instead.

## ElementName<sup>(deprecated)</sup>

> **NOTE**
>
> This API has been supported since API version 7 and deprecated since API version 9. You are advised to use [bundleManager-ElementName](js-apis-bundleManager-elementName.md#elementname-1) instead.

ElementName information, which identifies the basic information of an ability and can be obtained through [Context.getElementName](js-apis-inner-app-context.md#contextgetelementname7).

**System capability**: SystemCapability.BundleManager.BundleFramework



| Name                    | Type    | Read-Only| Optional| Description                      |
| ----------------------- | ---------| ---- | ---- | ------------------------- |
| deviceId                | string   | No  | Yes  | Device ID.                  |
| bundleName              | string   | No  | No | Bundle name.         |
| abilityName             | string   | No  | No | Ability name.              |
| uri                     | string   | No  | Yes | Resource ID.                |
| shortName               | string   | No  | Yes | Short name of the ability.              |