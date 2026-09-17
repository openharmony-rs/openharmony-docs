# isOpenTouchGuideSync

## Modules to Import

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { AccessibilityEventType, AccessibilityAction, FocusMoveResultCode, InjectActionType, AccessibilityFocusScene, FocusRuleType, OperateVirtualNodeResult, AccessibilitySourceType } from '@kit.AccessibilityKit';
```

## isOpenTouchGuideSync

```TypeScript
function isOpenTouchGuideSync(): boolean
```

Checks whether touch guide mode is enabled.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Vision

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether touch guide mode is enabled. Returns **true** if touch guide mode is enabled; returns **false** otherwise. |

**Examples**

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';

let status: boolean = accessibility.isOpenTouchGuideSync();
```
