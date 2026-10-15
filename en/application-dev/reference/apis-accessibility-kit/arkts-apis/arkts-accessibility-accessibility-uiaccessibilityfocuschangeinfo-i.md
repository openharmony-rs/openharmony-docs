# UIAccessibilityFocusChangeInfo

```TypeScript
interface UIAccessibilityFocusChangeInfo
```

Accessibility focus change information in an app.

**Since:** 26.0.1

<!--Device-accessibility-interface UIAccessibilityFocusChangeInfo--><!--Device-accessibility-interface UIAccessibilityFocusChangeInfo-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## Modules to Import

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { AccessibilityEventType, AccessibilityAction, FocusMoveResultCode, InjectActionType, AccessibilityFocusScene, FocusRuleType, OperateVirtualNodeResult, AccessibilitySourceType, UIRect, UIAccessibilityElement } from '@kit.AccessibilityKit';
```

## focusedElement

```TypeScript
focusedElement?: UIAccessibilityElement
```

The accessibility element that gains focus in this focus change.

**Type:** [UIAccessibilityElement](arkts-accessibility-accessibility-uiaccessibilityelement-i.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIAccessibilityFocusChangeInfo-focusedElement?: UIAccessibilityElement--><!--Device-UIAccessibilityFocusChangeInfo-focusedElement?: UIAccessibilityElement-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## unfocusedElement

```TypeScript
unfocusedElement?: UIAccessibilityElement
```

The accessibility element that loses focus in this focus change.

**Type:** [UIAccessibilityElement](arkts-accessibility-accessibility-uiaccessibilityelement-i.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIAccessibilityFocusChangeInfo-unfocusedElement?: UIAccessibilityElement--><!--Device-UIAccessibilityFocusChangeInfo-unfocusedElement?: UIAccessibilityElement-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core
