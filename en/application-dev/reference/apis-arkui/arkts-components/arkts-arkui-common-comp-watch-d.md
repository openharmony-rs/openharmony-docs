# @Watch

```TypeScript
declare const Watch: (value: string) => PropertyDecorator
```

**\@Watch** is used in [state management V1](../../../ui/state-management/arkts-state-management-overview.md) to listen for changes to state variables and trigger specified callback functions when the variables change. It applies to scenarios where linked logic, data synchronization, or derived value calculation needs to be automatically executed when a state variable changes.

For details, see [@Watch Decorator: Getting Notified of State Variable Changes](../../../ui/state-management/arkts-watch.md).

value: Name of the callback function for listening to changes in the state variable. The function signature is **(propertyName: string) =&gt; void**, where **propertyName** indicates the name of the changed property. PropertyDecorator: Property decorator. You do not need to concern yourself with this return value.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-unnamed-declare const Watch: (value: string) => PropertyDecorator--><!--Device-unnamed-declare const Watch: (value: string) => PropertyDecorator-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
