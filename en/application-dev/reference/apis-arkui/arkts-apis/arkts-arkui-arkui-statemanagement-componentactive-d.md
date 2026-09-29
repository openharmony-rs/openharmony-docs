# @ComponentActive

```TypeScript
export declare const ComponentActive: MethodDecorator
```

After a custom component transitions from the inactive state to the active state, the function decorated by **\@ComponentActive** is called. In the component reuse and recycling scenario, when a cached component is reused (that is, re-added to the node tree from the reuse pool), the component transitions from the inactive state to the active state, triggering this callback.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-unnamed-export declare const ComponentActive: MethodDecorator--><!--Device-unnamed-export declare const ComponentActive: MethodDecorator-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
