# @ComponentRecycle

```TypeScript
export declare const ComponentRecycle: MethodDecorator
```

After a component is recycled, the recycling operations such as resource release defined in the app are performed first. After the recycling is complete, the function decorated by **\@ComponentRecycle** is called, that is, it is triggered in the stage from **[CustomComponentLifecycleState](arkts-arkui-arkui-statemanagement-customcomponentlifecyclestate-e.md).BUILT** to **[CustomComponentLifecycleState](arkts-arkui-arkui-statemanagement-customcomponentlifecyclestate-e.md).RECYCLED**. Then the component is frozen to avoid UI updates while the component is in the reuse pool. Finally, recycling recursively traverses all child components, and for each child component that completes recycling, the function decorated by **\@ComponentRecycle** in the child component is called.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-unnamed-export declare const ComponentRecycle: MethodDecorator--><!--Device-unnamed-export declare const ComponentRecycle: MethodDecorator-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
