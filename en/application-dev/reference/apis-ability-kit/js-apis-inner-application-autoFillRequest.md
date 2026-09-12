# AutoFillRequest

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @hanchen45; @Luobniz21-->
<!--Designer: @ccllee1-->
<!--Tester: @lixueqing513-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=acf576bbf198928bef408f56b97d213fc0bc0354 translatedAt=2026-09-03T11:46:56.826Z pushedAt=2026-09-05T10:47:30.691Z -->

This module provides the page data in auto-fill and auto-save scenarios, as well as the result returned when auto-fill fails.

**Since:** 26.0.0

## Modules to Import

```ts
import { autoFillManager } from '@kit.AbilityKit';
```

## FillRequest

Auto-fill request information.

**Since:** 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Model restriction:** This API can be used only in the stage model.

| Name        | Type                                                                    | Read-only | Optional | Description           |
| ----------- | ----------------------------------------------------------------------- | ---- | ---- | ------------- |
| type        | [AutoFillType](js-apis-inner-application-autoFillType.md)               | No   | No   | Auto-fill type. |
| viewData    | [ViewData](js-apis-inner-application-viewData.md)                       | No   | No   | Page data. |
| triggerType | [AutoFillTriggerType](js-apis-inner-application-autoFillTriggerType.md) | No   | Yes  | Type for triggering the auto-fill service. |

## SaveRequest

Auto-save request information.

**Since:** 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Model restriction:** This API can be used only in the stage model.

| Name     | Type                                              | Read-only | Optional | Description |
| -------- | ------------------------------------------------- | --------- | -------- | ----------- |
| viewData | [ViewData](js-apis-inner-application-viewData.md) | No        | No       | Page data.  |

## FillFailureResult

Auto-fill failure result.

**Since:** 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Model restriction:** This API can be used only in the stage model.

| Name    | Type   | Read-only | Optional | Description      |
| ------- | ------ | --------- | -------- | ---------------- |
| errCode | number | No        | No       | Error code of the auto-fill failure. |
