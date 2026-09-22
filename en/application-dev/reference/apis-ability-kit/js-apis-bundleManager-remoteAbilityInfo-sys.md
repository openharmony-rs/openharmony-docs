# RemoteAbilityInfo (System API)
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @memghaiyang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=3a7b8d1fce741c2abccde7cccac39375139c4568 translatedAt=2026-09-03T11:17:00.912Z pushedAt=2026-09-05T10:47:30.588Z -->

The module provides information about a remote ability, which can be obtained through [distributedBundle.getRemoteAbilityInfo](js-apis-distributedBundleManager-sys.md#distributedbundlemanagergetremoteabilityinfo).

> **NOTE**
>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs provided by this module are system APIs.

## RemoteAbilityInfo

 **System capability**: SystemCapability.BundleManager.DistributedBundleFramework

 **System API**: This is a system API.

| Name       | Type                                        | Read-Only| Optional| Description                   |
| ----------- | -------------------------------------------- | ---- | ---- | ----------------------- |
| elementName | [ElementName](js-apis-bundleManager-elementName.md) | Yes  | No  | Element name information of the remote ability.      |
| label       | string                                       | Yes  | No  | Label of the remote ability.  |
| icon        | string                                       | Yes   | No   | Icon information of the remote ability. |
