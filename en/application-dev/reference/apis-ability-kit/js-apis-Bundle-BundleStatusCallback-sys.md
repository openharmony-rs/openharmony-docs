# BundleStatusCallback (System API)
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @memghaiyang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=1bd317f06f1afd85920306c4a4cf71333749080f translatedAt=2026-09-03T11:03:28.010Z pushedAt=2026-09-05T10:47:30.518Z -->

The module provides callbacks for bundle status changes. The changes can be obtained through [innerBundleManager.on](js-apis-Bundle-InnerBundleManager-sys.md#innerbundlemanagerondeprecated).

> **NOTE**
>
> The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> This module is no longer maintained since API version 9, and no substitute API is available.
>
> This is a system API.

## BundleStatusCallback<sup>(deprecated)<sup>

> **NOTE**
>
> This API has been supported since API version 8 and deprecated since API version 9. No substitute is provided.

**System API**: This is a system API.

**System capability**: SystemCapability.BundleManager.BundleFramework

| Type  | Callback                                         | Description                                  |
| ------ | --------------------------------------------- | -------------------------------------- |
| add    | (bundleName : string, userId: number) => void | Used to obtain information when a bundle is installed.|
| update | (bundleName : string, userId: number) => void | Used to obtain information when a bundle is updated.|
| remove | (bundleName : string, userId: number) => void | Used to obtain information when a bundle is uninstalled.|