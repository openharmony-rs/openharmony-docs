# @Local

```TypeScript
declare const Local: PropertyDecorator
```

**\@Local** is used in [state management V2](../../../ui/state-management/arkts-state-management-overview.md) to represent the internal state of components, enabling the observation of variables within custom components. It is applicable to scenarios where partial states (such as counters and switch states) need to be maintained and observed within custom components. Using **\@Local** can simplify the internal state management logic of components. When the state changes, the UI is automatically refreshed without manual management.

For details, see [@Local Decorator: Representing the Internal State of Components](../../../ui/state-management/arkts-new-local.md).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

<!--Device-unnamed-declare const Local: PropertyDecorator--><!--Device-unnamed-declare const Local: PropertyDecorator-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
