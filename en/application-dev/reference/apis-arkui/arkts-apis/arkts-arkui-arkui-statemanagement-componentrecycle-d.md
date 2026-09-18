# @ComponentRecycle

```TypeScript
export declare const ComponentRecycle: MethodDecorator
```

Decorates a function that is called when the necessary recycling operations defined in the application are performed. That is, this function is triggered when the component status changes from **CustomComponentLifecycleState.BUILT** to **CustomComponentLifecycleState.RECYCLED**. At last, the function decorated by **@ComponentRecycle** recursively traverses all child components, and the **@ComponentRecycle** decorated function in each recycled child component will be called.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
