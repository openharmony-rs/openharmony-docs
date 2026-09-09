# ApplicationInfo (System API)
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @memghaiyang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=b1e39aedfe1dc3f164c93ee083af03b62dfe063f translatedAt=2026-09-03T11:09:00.166Z pushedAt=2026-09-05T10:47:30.548Z -->

The module defines the application information. An application can obtain its own application information through [bundleManager.getBundleInfoForSelf](js-apis-bundleManager.md#bundlemanagergetbundleinfoforself), with **GET_BUNDLE_INFO_WITH_APPLICATION** passed in to [bundleFlags](js-apis-bundleManager.md#bundleflag).

> **NOTE**
>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> This page contains only the system APIs of this module. For details about other public APIs, see [ApplicationInfo](js-apis-bundleManager-applicationInfo.md).

## Modules to Import

```ts
import { bundleManager } from '@kit.AbilityKit';
```

## ApplicationInfo

**System capability**: SystemCapability.BundleManager.BundleFramework.Core

**System API**: This is a system API.

| Name     | Type          | Read-Only| Optional| Description                       |
| --------- | -------------- | ---- | ---- | --------------------------- |
| flags<sup>12+</sup>    | number    | Yes  | Yes  | Status set between the current application and the current user. Each bit indicates a specific Boolean status. For details about the values, see [ApplicationInfoFlag](js-apis-bundleManager-sys.md#applicationinfoflag12).<br>**System API**: This property can be used in system APIs since API version 12.|


## PreinstalledApplicationInfo

**System capability**: SystemCapability.BundleManager.BundleFramework.Core

**System API**: This is a system API.

| Name     | Type          | Read-Only| Optional| Description                       |
| --------- | -------------- | ---- | ---- | --------------------------- |
| bundleName<sup>12+</sup> | string         | Yes   | No   | Name of the application package.                |
| moduleName<sup>12+</sup> | string         | Yes   | No   | Module name of the application package. Returns the moduleName of the entry module. If no entry module exists, returns the moduleName of the feature module.            |
| iconId<sup>12+</sup> | number         | Yes   | No   | Application icon ID.           |
| labelId<sup>12+</sup> | number         | Yes   | No   | Application label ID.            |
| descriptionId<sup>24+</sup> | number         | Yes   | Yes   | App description ID.<br>**Model restriction:** This API can be used only in the stage model.            |