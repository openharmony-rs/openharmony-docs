# @ComponentInactive

```TypeScript
export declare const ComponentInactive: MethodDecorator
```

After a custom component transitions from the active state to the inactive state, the function decorated by **\@ComponentInactive** is called. In the component reuse and recycling scenario, when a component is recycled to the reuse pool, the component transitions from the active state to the inactive state, triggering this callback.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-unnamed-export declare const ComponentInactive: MethodDecorator--><!--Device-unnamed-export declare const ComponentInactive: MethodDecorator-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
