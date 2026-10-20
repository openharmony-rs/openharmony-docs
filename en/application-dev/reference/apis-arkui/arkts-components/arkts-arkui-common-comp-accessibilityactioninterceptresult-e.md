# AccessibilityActionInterceptResult

```TypeScript
declare enum AccessibilityActionInterceptResult
```

Enumerates possible results for accessibility action interception.

**Since:** 20

<!--Device-unnamed-declare enum AccessibilityActionInterceptResult--><!--Device-unnamed-declare enum AccessibilityActionInterceptResult-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ACTION_CONTINUE

```TypeScript
ACTION_CONTINUE = 1
```

Does not intercept the accessibility control operation received by the current component. After the callback handling is complete, the current component is allowed to respond to the accessibility control operation and execute its processing logic.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**Widget capability:** This API can be used in ArkTS widgets since API version 20.

<!--Device-AccessibilityActionInterceptResult-ACTION_CONTINUE = 1--><!--Device-AccessibilityActionInterceptResult-ACTION_CONTINUE = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ACTION_INTERCEPT

```TypeScript
ACTION_INTERCEPT = 0
```

Intercepts the accessibility control action received by the current component. After the callback processing is complete, the component won't respond.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**Widget capability:** This API can be used in ArkTS widgets since API version 20.

<!--Device-AccessibilityActionInterceptResult-ACTION_INTERCEPT = 0--><!--Device-AccessibilityActionInterceptResult-ACTION_INTERCEPT = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ACTION_RISE

```TypeScript
ACTION_RISE = 2
```

Does not intercept the accessibility control operation received by the current component. After the callback handling is complete, the component still needs to respond and execute its processing logic, and the accessibility control operation information is passed to the parent component. When the information is passed to the next component that uses onAccessibilityActionIntercept, the callback registered in that component is triggered, but the processing logic of that component is not triggered. After the processing is complete, ACTION_RISE can continue to be used to pass the accessibility control operation information to the parent component.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**Widget capability:** This API can be used in ArkTS widgets since API version 20.

<!--Device-AccessibilityActionInterceptResult-ACTION_RISE = 2--><!--Device-AccessibilityActionInterceptResult-ACTION_RISE = 2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
