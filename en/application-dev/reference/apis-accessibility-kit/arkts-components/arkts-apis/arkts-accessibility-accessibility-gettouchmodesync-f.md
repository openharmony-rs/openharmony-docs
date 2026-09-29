# getTouchModeSync

## Modules to Import

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { AccessibilityEventType, AccessibilityAction, FocusMoveResultCode, InjectActionType, AccessibilityFocusScene, FocusRuleType, OperateVirtualNodeResult, AccessibilitySourceType } from '@kit.AccessibilityKit';
```

## getTouchModeSync

```TypeScript
function getTouchModeSync(): string
```

Obtains the single-tap/double-tap operation mode in touch guide mode. This can be used to adjust the app's interaction response mode based on the current operation mode (for example, responding directly to taps in single- tap mode, or requiring double-tap confirmation in double-tap mode).

**Since:** 20

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 23.

**Widget capability (ArkTS-Dyn only) :** This API can be used in ArkTS widgets since version 23.

<!--Device-accessibility-function getTouchModeSync(): string--><!--Device-accessibility-function getTouchModeSync(): string-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | Touch mode.<br>- **singleTouchMode**: Single-touch mode. <br>- **doubleTouchMode**: Double-touch mode. <br>- **none**: Touch guide mode is disabled. |

**Examples**
