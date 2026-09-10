# RemoteAbilityInfo (System API)
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @memghaiyang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=3a7b8d1fce741c2abccde7cccac39375139c4568 translatedAt=2026-09-03T11:07:48.378Z pushedAt=2026-09-05T10:47:30.542Z -->

The module provides information about a remote ability.

> **NOTE**
>
> The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> This module is no longer maintained since API version 9. You are advised to use [RemoteAbilityInfo](js-apis-bundleManager-remoteAbilityInfo-sys.md) instead.
>
> This is a system API.

## RemoteAbilityInfo<sup>(deprecated)<sup>

> **NOTE**
>
> This API has been supported since API version 8 and deprecated since API version 9. You are advised to use [bundleManager-RemoteAbilityInfo](js-apis-bundleManager-remoteAbilityInfo-sys.md#remoteabilityinfo) instead.

 **System capability**: SystemCapability.BundleManager.DistributedBundleFramework

 **System API**: This is a system API.

| Name        | Type                                         | Read-only | Optional | Description                    |
| ----------- | -------------------------------------------- | --------- | -------- | ------------------------------ |
| elementName | [ElementName](js-apis-bundle-ElementName.md) | Yes       | No       | Element resource information of the ability. |
| label       | string                                       | Yes       | No       | Name of the ability.           |
| icon        | string                                       | Yes       | No       | Icon information of the ability. |
