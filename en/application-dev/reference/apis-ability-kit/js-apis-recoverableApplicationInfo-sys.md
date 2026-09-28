# RecoverableApplicationInfo (System API)
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @memghaiyang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=1bd317f06f1afd85920306c4a4cf71333749080f translatedAt=2026-09-03T12:28:14.638Z pushedAt=2026-09-05T10:47:30.931Z -->

The module defines the information about a preinstalled application that can be restored after being uninstalled. The information can be obtained through [bundleManager.getRecoverableApplicationInfo](./js-apis-bundleManager-sys.md#bundlemanagergetrecoverableapplicationinfo11).

> **NOTE**
>
> The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs provided by this module are system APIs.

## Modules to Import

```ts
import { bundleManager } from '@kit.AbilityKit';
```

## RecoverableApplicationInfo

Defines the information about a preinstalled application that can be restored after being uninstalled.

**System API**: This is a system API.

**System capability**: SystemCapability.BundleManager.BundleFramework.Core

| Name            | Type                          | Read-Only| Optional| Description                  |
| ---------------- | ------------------------------ | ---- | ---- | ---------------------- |
| bundleName       | string                         | Yes  | No  | Bundle name.      |
| moduleName       | string                         | Yes  | No  | Module name.|
| labelId          | number                         | Yes  | No  | ID of the module label.    |
| iconId           | number                         | Yes  | No  | ID of the module icon.   |
| systemApp<sup>12+</sup>       | boolean                        | Yes  | No  | Whether the application is a system application. **true** if it is a system application, **false** otherwise. |
| bundleType<sup>12+</sup>       |[bundleManager.BundleType](js-apis-bundleManager.md#bundletype)             | Yes  | No  | Bundle type.                               |
| codePaths<sup>12+</sup>        | Array\<string>                 | Yes  | No  | Installation directory of the application.         |