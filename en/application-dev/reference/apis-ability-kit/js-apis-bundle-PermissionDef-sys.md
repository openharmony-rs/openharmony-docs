# PermissionDef (System API)
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @memghaiyang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=1bd317f06f1afd85920306c4a4cf71333749080f translatedAt=2026-09-03T11:07:02.581Z pushedAt=2026-09-05T10:47:30.538Z -->

The module provides permission details defined in the configuration file.

> **NOTE**
>
> The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> Since API version 9, this module is no longer maintained. You are advised to use [PermissionDef](js-apis-bundleManager-permissionDef-sys.md) instead.
>
> This module is a system API.

## **PermissionDef**<sup>(deprecated)<sup>

> **NOTE**
>
> Supported since API version 8 and deprecated since API version 9. You are advised to use [PermissionDef](js-apis-bundleManager-permissionDef-sys.md#permissiondef) instead.

 **System capability**: SystemCapability.BundleManager.BundleFramework

 **System API**: This is a system API.

| Name          | Type  | Read-Only| Optional| Description          |
| -------------- | ------ | ---- | ---- | -------------- |
| permissionName | string | No  | No  | Name of the permission.  |
| grantMode      | number | No  | No  | Grant mode of the permission. The value **0** means that the system automatically grants the permission after the application installation, and **1** means that the application needs to dynamically request the permission from the user.|
| labelId        | number | No  | No  | ID of the permission label.  |
| descriptionId  | number | No  | No  | ID of the permission description.  |