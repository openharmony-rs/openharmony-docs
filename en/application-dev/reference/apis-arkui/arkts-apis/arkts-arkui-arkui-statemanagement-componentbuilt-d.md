# @ComponentBuilt

```TypeScript
export declare const ComponentBuilt: MethodDecorator
```

The function decorated by **\@ComponentBuilt** is called after the **build()** function of a custom component is executed for the first time, that is, it is triggered in the stage from **[CustomComponentLifecycleState](arkts-arkui-arkui-statemanagement-customcomponentlifecyclestate-e.md).APPEARED** to **[CustomComponentLifecycleState](arkts-arkui-arkui-statemanagement-customcomponentlifecyclestate-e.md).BUILT**. You can implement functions that do not affect the actual UI, such as event data reporting, in this phase.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-unnamed-export declare const ComponentBuilt: MethodDecorator--><!--Device-unnamed-export declare const ComponentBuilt: MethodDecorator-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
