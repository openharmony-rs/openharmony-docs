# OverlayModuleInfo
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @memghaiyang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=1bd317f06f1afd85920306c4a4cf71333749080f translatedAt=2026-09-03T11:16:27.428Z pushedAt=2026-09-05T10:47:30.584Z -->

The OverlayModuleInfo information can be obtained through [overlay.getOverlayModuleInfo](js-apis-overlay.md#overlaygetoverlaymoduleinfo) to get the OverlayModuleInfo information of the module with the overlay feature in the current application.

> **NOTE**
> The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

``` ts
import { overlay } from '@kit.AbilityKit';
```

## OverlayModuleInfo

**System capability**: SystemCapability.BundleManager.BundleFramework.Core

| Name                 | Type                                               | Read-Only| Optional| Description                                           |
| --------------------- | ---------------------------------------------------| ---- | ---- | ---------------------------------------------- |
| bundleName            | string                                             | Yes   | No   | Bundle name of the application to which the overlay feature module belongs.           |
| moduleName            | string                                             | Yes   | No   | Name of the overlay feature module.                       |
| targetModuleName      | string                                             | Yes   | No   | Name of the target module on which the overlay feature module takes effect, indicating the module whose resources are to be replaced by the current overlay package.        |
| priority              | number                                             | Yes   | No   | Priority of the overlay feature module. The value is an integer ranging from 1 to 100. A larger value indicates a higher priority.    |
| state                 | number                                             | Yes   | No   | Enabled or disabled state of the overlay feature module. The value is an integer ranging from 0 to 2, where 0 indicates the disabled state, 1 indicates the enabled state, and 2 indicates the invalid state. |