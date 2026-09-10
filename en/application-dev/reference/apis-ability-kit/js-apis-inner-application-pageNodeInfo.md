# PageNodeInfo

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @hanchen45-->
<!--Designer: @ccllee1-->
<!--Tester: @lixueqing513-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=e2e4d688beb0becfa2a64d71411845578aee3b47 translatedAt=2026-09-03T12:01:43.725Z pushedAt=2026-09-05T10:47:30.854Z -->

PageNodeInfo describes the page node information in auto-fill scenarios, including key data such as the node ID, auto-fill type, current value, placeholder text, coordinate position, and focus state. It is used by the auto-fill service to obtain page control information for performing fill operations.

**Since:** 26.0.0

## Modules to Import

```ts
import { autoFillManager } from '@kit.AbilityKit';
```

## PageNodeInfo

**Since:** 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Model restriction:** This API can be used only in the stage model.

| Name         | Type    | Read-only | Optional | Description           |
| ------------ | ------- | ---- | ---- | ------------- |
| id           | number  | No   | No   | ID of the page node. |
| autoFillType | [AutoFillType](js-apis-inner-application-autoFillType.md) | No   | No   | Auto-fill type of the page node. |
| value        | string  | No   | No   | Value currently displayed on the page node or entered by the user. This value is filled into the corresponding node during auto-fill. |
| placeholder  | string  | No   | Yes   | Placeholder text of the page node, usually displayed in the input control to prompt the user for the expected input. It can help the auto-fill service identify the fill type. |
| rect         | [AutoFillRect](js-apis-inner-application-autoFillRect.md) | No   | No   | Coordinates, width, and height of the current node. |
| isFocus      | boolean | No   | No   | Whether the current node has focus. The value true indicates that the current node has focus, and false indicates the opposite. |
