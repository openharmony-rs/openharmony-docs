# offUIAccessibilityFocusChanged

## Modules to Import

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { AccessibilityEventType, AccessibilityAction, FocusMoveResultCode, InjectActionType, AccessibilityFocusScene, FocusRuleType, OperateVirtualNodeResult, AccessibilitySourceType, UIRect, UIAccessibilityElement } from '@kit.AccessibilityKit';
```

## offUIAccessibilityFocusChanged

```TypeScript
function offUIAccessibilityFocusChanged(callback?: Callback<UIAccessibilityFocusChangeInfo>): void
```

Unsubscribes from accessibility focus change events in the app.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-accessibility-function offUIAccessibilityFocusChanged(callback?: Callback<UIAccessibilityFocusChangeInfo>): void--><!--Device-accessibility-function offUIAccessibilityFocusChanged(callback?: Callback<UIAccessibilityFocusChangeInfo>): void-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[UIAccessibilityFocusChangeInfo](arkts-accessibility-accessibility-uiaccessibilityfocuschangeinfo-i.md)&gt; | No | Callback for accessibility focus change events. It must be the same as the callback used in [accessibility.onUIAccessibilityFocusChanged](arkts-accessibility-accessibility-onuiaccessibilityfocuschanged-f.md). If this parameter is not specified, all registered events are unsubscribed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9300000](../errorcode-accessibility.md#9300000-accessibility-system-service-abnormal) | System abnormality. Possible causes:<br>1.Internal operation failed. <br>2.Failed to obtain the required service or client object (null pointer). <br>3.The listener or observer is not registered. |
