# AutoFillRect

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @hanchen45-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=27415df324fbfef3fba7ae1b59fc2bc2dafaaa17 translatedAt=2026-11-04T09:54:35.239Z pushedAt=2026-11-04T09:59:36.501Z nl=1 -->

Rectangular area used for auto-fill.

**Since**: 26.0.0

## Modules to Import

```ts
import { autoFillManager } from '@kit.AbilityKit';
```

## AutoFillRect

**Since**: 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Model restriction:** This API can be used only in the stage model.

| Name   | Type   | Read-Only | Optional | Description                                                |
| ------ | ------ | ---- | ---- | -------------------------------------------------- |
| left   | number | No   | No   | Distance between the AutoFill form or page node and the left edge of the page, in px. |
| top    | number | No   | No   | Distance between the AutoFill form or page node and the top edge of the page, in px. |
| height | number | No   | No   | Height of the AutoFill form or page node, in px. |
| width  | number | No   | No   | Width of the AutoFill form or page node, in px. |
