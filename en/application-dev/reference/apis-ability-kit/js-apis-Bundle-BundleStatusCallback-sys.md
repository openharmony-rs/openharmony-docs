# BundleStatusCallback (System API)
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @kongjing2-->
<!--Adviser: @Brilliantry_Rui-->

The module provides callbacks for bundle status changes. The changes can be obtained through [innerBundleManager.on](js-apis-Bundle-InnerBundleManager-sys.md#innerbundlemanagerondeprecated).

> **NOTE**
>
> The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module have been deprecated since API version 9. No substitute is provided.
> 
> The APIs provided by this module are system APIs.

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
