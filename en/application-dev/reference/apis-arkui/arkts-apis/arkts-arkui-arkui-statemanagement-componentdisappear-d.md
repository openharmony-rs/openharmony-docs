# @ComponentDisappear

```TypeScript
export declare const ComponentDisappear: MethodDecorator
```

Decorates a function that is called when the custom component is destructed. You are advised not to change state variables in this function. Modifying the **@Link** decorated variable may lead to unstable application behavior.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
