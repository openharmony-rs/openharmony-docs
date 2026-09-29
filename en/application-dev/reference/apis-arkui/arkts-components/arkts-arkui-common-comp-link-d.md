# @Link

```TypeScript
declare const Link: PropertyDecorator
```

**\@Link** is used for [state management V1](../../../ui/state-management/arkts-state-management-overview.md) to receive the reference of the state variable passed by the parent component and establish two-way data binding between the parent and child components. It is applicable to scenarios where the parent component's state needs to be directly changed in the child component and the communication between the parent and child components needs to be simplified.

For details, see [@Link Decorator: Implementing Two-Way Synchronization Between Parent and Child Components](../../../ui/state-management/arkts-link.md).

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-unnamed-declare const Link: PropertyDecorator--><!--Device-unnamed-declare const Link: PropertyDecorator-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
