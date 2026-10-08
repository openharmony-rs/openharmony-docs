# AutoFillRect

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @hanchen45-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=e2e4d688beb0becfa2a64d71411845578aee3b47 translatedAt=2026-09-03T11:44:59.686Z pushedAt=2026-09-05T10:47:30.687Z -->

Rectangular area used for auto-fill.

**Since:** 26.0.0

## Modules to Import

```ts
import { autoFillManager } from '@kit.AbilityKit';
```

## AutoFillRect

**Since:** 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Model restriction:** This API can be used only in the stage model.

| Name   | Type   | Read-only | Optional | Description                                                |
| ------ | ------ | ---- | ---- | -------------------------------------------------- |
| left   | number | No   | No   | Distance between the AutoFill form or page node and the left edge of the page, in pixels. |
| top    | number | No   | No   | Distance between the AutoFill form or page node and the top edge of the page, in pixels. |
| height | number | No   | No   | Height of the AutoFill form or page node, in pixels. |
| width  | number | No   | No   | Width of the AutoFill form or page node, in pixels. |
