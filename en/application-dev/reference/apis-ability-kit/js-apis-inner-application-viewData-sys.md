# ViewData (System API)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @hanchen45; @Luobniz21-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=e2e4d688beb0becfa2a64d71411845578aee3b47 translatedAt=2026-09-03T12:19:09.673Z pushedAt=2026-09-05T10:47:30.897Z -->

The module defines the view data used for auto-fill.

> **NOTE**
>
> The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> This page contains only the system APIs of this module. For details about other public APIs, see [ViewData](js-apis-inner-application-viewData.md).

## Modules to Import

```ts
import { autoFillManager } from '@kit.AbilityKit';
```

## ViewData

**System capability**: SystemCapability.Ability.AbilityRuntime.AbilityCore

**Model restriction:** This API can be used only in the stage model.

| Name       | Type                | Read-Only| Optional| Description                                                        |
| ----------- | ------------------- | ---- | ---- | ------------------------------------------------------------ |
| moduleName    | string            | No   | No   | Module name, used to specify the module to which the auto-fill data belongs.          |
| abilityName   | string            | No   | No   | Ability name, used to specify the ability to which the auto-fill data belongs.    |
| isUserSelected<sup>12+</sup> | boolean | No  | No  | Whether the content to be filled is selected by the user. **true** if the content is selected by the user, and **false** otherwise.|
| isOtherAccount<sup>12+</sup> | boolean | No  | No  | Whether to display other account information saved in the password box for the user to select. **true** to display, **false** otherwise.|
