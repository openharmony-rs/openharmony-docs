# isScreenReaderOpenSync

## Modules to Import

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { AccessibilityEventType, AccessibilityAction, FocusMoveResultCode, InjectActionType, AccessibilityFocusScene, FocusRuleType, OperateVirtualNodeResult, AccessibilitySourceType } from '@kit.AccessibilityKit';
```

## isScreenReaderOpenSync

```TypeScript
function isScreenReaderOpenSync(): boolean
```

Checks whether screen reader mode is enabled.

**Since:** 18

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 23.

**Widget capability (ArkTS-Dyn only) :** This API can be used in ArkTS widgets since version 23.

<!--Device-accessibility-function isScreenReaderOpenSync(): boolean--><!--Device-accessibility-function isScreenReaderOpenSync(): boolean-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Vision

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the screen reader is enabled. Returns **true** if the screen reader is enabled; returns **false** otherwise. |

**Examples**

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';

let status: boolean = accessibility.isScreenReaderOpenSync();
```
