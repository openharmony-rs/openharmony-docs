# AccessibilityActionInterceptCallback

```TypeScript
declare type AccessibilityActionInterceptCallback = (action: AccessibilityAction) => AccessibilityActionInterceptResult
```

Defines the callback type used in accessibility action intercept. The value of action indicates the accessibility action type.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**Widget capability:** This API can be used in ArkTS widgets since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| action | [AccessibilityAction](arkts-arkui-accessibilityaction-e.md) | Yes | the enum of accessibility action type. |

**Return value:**

| Type | Description |
| --- | --- |
| [AccessibilityActionInterceptResult](arkts-arkui-accessibilityactioninterceptresult-e.md) | the result of continuing to execute the action or interrupting it or bubbling up |
