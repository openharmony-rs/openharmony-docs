# getFocusedUIAccessibilityElement

## Modules to Import

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { AccessibilityEventType, AccessibilityAction, FocusMoveResultCode, InjectActionType, AccessibilityFocusScene, FocusRuleType, OperateVirtualNodeResult, AccessibilitySourceType, UIRect, UIAccessibilityElement } from '@kit.AccessibilityKit';
```

## getFocusedUIAccessibilityElement

```TypeScript
function getFocusedUIAccessibilityElement(): Promise<UIAccessibilityElement | undefined>
```

Obtain the accessibility focus elements within the application. This API uses a promise to return the result.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-accessibility-function getFocusedUIAccessibilityElement(): Promise<UIAccessibilityElement | undefined>--><!--Device-accessibility-function getFocusedUIAccessibilityElement(): Promise<UIAccessibilityElement | undefined>-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[UIAccessibilityElement](arkts-accessibility-accessibility-uiaccessibilityelement-i.md) &#124; undefined&gt; | Promise used to return the current accessibility focus element within the application; returns undefined if there is no accessibility focus. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9300000](../errorcode-accessibility.md#9300000-accessibility-system-service-abnormal) | System abnormality. Possible causes:<br>1.Internal operation failed. <br>2.Failed to obtain the required service or client object (null pointer). |
