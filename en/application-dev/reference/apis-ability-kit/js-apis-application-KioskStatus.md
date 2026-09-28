# KioskStatus (Kiosk Status Information)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zhu-feimo-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=9b45198dbdb6f53f8bf0896d62425626f2442690 translatedAt=2026-09-03T11:00:52.789Z pushedAt=2026-09-05T10:47:30.505Z -->

The module provides the kiosk status information, including whether the system is in kiosk mode and the information about the application in kiosk mode.

> **NOTE**
>
> The initial APIs of this module are supported since API version 20. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.

## KioskStatus

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name                 | Type                   | Read-Only| Optional| Description                                                 |
| --------------------- | ---------------------- | ---- | ---- | ---------------------------------------------------- |
| isKioskMode           | boolean                | No  | No  | Whether the system is in kiosk mode. **true** if in kiosk mode, **false** otherwise.|
| kioskBundleName       | string                 | No  | No  | Bundle name of the application in kiosk mode.                         |
| kioskBundleUid        | number                 | No   | No   | UID of the application that enters Kiosk mode. It is assigned by the system and is a positive integer.    |
