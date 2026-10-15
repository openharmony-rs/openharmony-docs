# onUIAccessibilityFocusChanged

## Modules to Import

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { AccessibilityEventType, AccessibilityAction, FocusMoveResultCode, InjectActionType, AccessibilityFocusScene, FocusRuleType, OperateVirtualNodeResult, AccessibilitySourceType, UIRect, UIAccessibilityElement } from '@kit.AccessibilityKit';
```

## onUIAccessibilityFocusChanged

```TypeScript
function onUIAccessibilityFocusChanged(callback: Callback<UIAccessibilityFocusChangeInfo>): void
```

Subscribes to accessibility focus change events in the app.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-accessibility-function onUIAccessibilityFocusChanged(callback: Callback<UIAccessibilityFocusChangeInfo>): void--><!--Device-accessibility-function onUIAccessibilityFocusChanged(callback: Callback<UIAccessibilityFocusChangeInfo>): void-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[UIAccessibilityFocusChangeInfo](arkts-accessibility-accessibility-uiaccessibilityfocuschangeinfo-i.md)&gt; | Yes | Callback function. This function is used to notify the focus change information when the accessibility focus changes in an application. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9300000](../errorcode-accessibility.md#9300000-accessibility-system-service-abnormal) | System abnormality. Possible causes:<br>1.Internal operation failed. <br>2.Failed to obtain the required service or client object (null pointer). |
