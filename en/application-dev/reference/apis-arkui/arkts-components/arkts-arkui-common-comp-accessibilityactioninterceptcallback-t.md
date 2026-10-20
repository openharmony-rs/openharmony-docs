# AccessibilityActionInterceptCallback

```TypeScript
declare type AccessibilityActionInterceptCallback = (action: AccessibilityAction) => AccessibilityActionInterceptResult
```

Defines the callback type used in onAccessibilityActionIntercept.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**Widget capability:** This API can be used in ArkTS widgets since API version 20.

<!--Device-unnamed-declare type AccessibilityActionInterceptCallback = (action: AccessibilityAction) => AccessibilityActionInterceptResult--><!--Device-unnamed-declare type AccessibilityActionInterceptCallback = (action: AccessibilityAction) => AccessibilityActionInterceptResult-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| action | [AccessibilityAction](arkts-arkui-common-comp-accessibilityaction-e.md) | Yes | Type of the accessibility control operation currently triggered. |

**Return value:**

| Type | Description |
| --- | --- |
| [AccessibilityActionInterceptResult](arkts-arkui-common-comp-accessibilityactioninterceptresult-e.md) | Result of intercepting an accessibility control operation, used to determine whether to intercept the accessibility control operation of the current component and the subsequent processing method. |
