# @ComponentReuse

```TypeScript
export declare const ComponentReuse: MethodDecorator
```

The function decorated by **\@ComponentReuse** is called when a reusable custom component is re-added to the node tree from the cache, that is, it is triggered in the stage from **[CustomComponentLifecycleState](arkts-arkui-arkui-statemanagement-customcomponentlifecyclestate-e.md).RECYCLED** to **[CustomComponentLifecycleState](arkts-arkui-arkui-statemanagement-customcomponentlifecyclestate-e.md).BUILT**, to receive the construction parameters of the component. Finally, reuse recursively traverses all child components, and for each child component that completes reuse, the function decorated by **\@ComponentReuse** in the child component is called.

> **NOTE:** 
> 
> - In a state management V1 component, the function decorated by **\@ComponentReuse** can have one input parameter or no parameter. The input parameter **params** is recommended to be of the
> **Record\&lt;string, Object \| undefined \| null\&gt;** type.
> 
> - In a state management V2 component, the function decorated by **\@ComponentReuse** has no input parameter.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-unnamed-export declare const ComponentReuse: MethodDecorator--><!--Device-unnamed-export declare const ComponentReuse: MethodDecorator-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
