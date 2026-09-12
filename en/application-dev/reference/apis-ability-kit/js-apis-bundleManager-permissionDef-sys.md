# PermissionDef (System API)
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @memghaiyang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=3a7b8d1fce741c2abccde7cccac39375139c4568 translatedAt=2026-09-03T11:16:25.742Z pushedAt=2026-09-05T10:47:30.582Z -->

The module provides permission details defined in the [module.json5](../../quick-start/module-configuration-file.md) file. The information can be obtained using [bundleManager.getPermissionDef](js-apis-bundleManager-sys.md#bundlemanagergetpermissiondef).

> **NOTE**
>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs provided by this module are system APIs.

## Modules to Import

```ts
import { bundleManager } from '@kit.AbilityKit';
```

## PermissionDef

**System capability**: SystemCapability.BundleManager.BundleFramework.Core

**System API**: This is a system API.

| Name          | Type  | Read-Only| Optional| Description          |
| -------------- | ------ | ---- | ---- | -------------- |
| permissionName | string | Yes  | No   | Permission name.   |
| grantMode      | number | Yes  | No  | [Grant mode of the permission](../../security/AccessToken/app-permission-mgmt-overview.md#authorization-mode). The value **0** means user authorization, and **1** means system authorization.|
| labelId        | number | Yes  | No   | Resource ID of the permission label, used to display the permission name.   |
| descriptionId  | number | Yes  | No   | Resource ID of the permission description.   |