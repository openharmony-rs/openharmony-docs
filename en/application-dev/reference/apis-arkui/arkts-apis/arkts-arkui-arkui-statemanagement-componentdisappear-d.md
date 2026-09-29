# @ComponentDisappear

```TypeScript
export declare const ComponentDisappear: MethodDecorator
```

The function decorated by **\@ComponentDisappear** is executed before a custom component is destroyed, that is, it is triggered when the component transitions to the **[CustomComponentLifecycleState](arkts-arkui-arkui-statemanagement-customcomponentlifecyclestate-e.md).DISAPPEARED** state. It is not recommended to change state variables in this function. In particular, modifying **\@Link** variables may cause unstable app behavior.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-unnamed-export declare const ComponentDisappear: MethodDecorator--><!--Device-unnamed-export declare const ComponentDisappear: MethodDecorator-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
