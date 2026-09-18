# @ComponentReuse

```TypeScript
export declare const ComponentReuse: MethodDecorator
```

Decorates a function that is called when a reusable custom component is re-added to the node tree from the cache, that is, when the component status changes from the **CustomComponentLifecycleState.RECYCLED** to **CustomComponentLifecycleState.BUILT** phase, to receive the constructor parameters. At last, the function decorated by **@ComponentReuse** recursively traverses all child components, and the **@ComponentReuse** decorated function in each reused child component will be called.

> **NOTE:** 
> 
> - The value of **params** is not **undefined** in the callback of the reused state management V1 component.
> 
> - The value of **params** is **undefined** in the callback of the reused state management V2 component.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
