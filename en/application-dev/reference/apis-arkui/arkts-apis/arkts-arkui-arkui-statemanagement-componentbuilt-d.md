# @ComponentBuilt

```TypeScript
export declare const ComponentBuilt: MethodDecorator
```

Decorates a function that is called after the **build()** function of the custom component is executed for the first time, that is, when the component status changes from **CustomComponentLifecycleState.APPEARED** to **CustomComponentLifecycleState.BUILT**. You can use this callback for actions that do not affect the UI, such as tracking data reporting.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
