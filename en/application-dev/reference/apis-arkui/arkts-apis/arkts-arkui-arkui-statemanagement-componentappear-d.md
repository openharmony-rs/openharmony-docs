# @ComponentAppear

```TypeScript
export declare const ComponentAppear: MethodDecorator
```

Decorates a function that is called after a new instance of the custom component is created and before the **build()** function is executed. This callback is similar to **aboutToAppear**. The difference is that the **@ComponentAppear** callback is triggered only when the custom component is in the **[CustomComponentLifecycleState](arkts-arkui-arkui-statemanagement-customcomponentlifecyclestate-e.md).INIT** state. The state variable can be changed in **@ComponentAppear**. The change will take effect in the subsequent **build()** function execution.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
