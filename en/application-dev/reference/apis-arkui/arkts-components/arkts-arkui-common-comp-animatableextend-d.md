# @AnimatableExtend

```TypeScript
declare const AnimatableExtend: MethodDecorator & ((value: Object) => MethodDecorator)
```

The @AnimatableExtend decorator is used to customize animatable property methods. Functions defined within this decorator are called on a frame-by-frame basis during the animation process until the animation ends.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
