# @ohos.ability.errorCode (ErrorCode)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @dsz2025-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=39c91f6014aebaf032e76cba1dba0db7318cd7f0 translatedAt=2026-09-03T09:27:20.997Z pushedAt=2026-09-05T10:47:30.169Z -->

The ErrorCode module defines the error codes that may be returned when an ability is started.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 6. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { ErrorCode } from '@kit.AbilityKit';
```

## ErrorCode

Enumerates the error codes that may be returned when an ability is started.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name                            | Value   | Description                                      |
| ------------------------------ | ---- | ---------------------------------------- |
| NO_ERROR         | 0    | The ability is started successfully.  |
| INVALID_PARAMETER | -1   | Invalid parameter.|
| ABILITY_NOT_FOUND | -2   | The ability is not found.|
| PERMISSION_DENY   | -3   | Permission denied.  |