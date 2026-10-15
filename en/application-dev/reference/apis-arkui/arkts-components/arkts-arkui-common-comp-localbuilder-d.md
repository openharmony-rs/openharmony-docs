# @LocalBuilder

```TypeScript
declare const LocalBuilder: MethodDecorator
```

\@LocalBuilder provides the same functionality as the local \@Builder, and can better determine the parent-child relationships of components and state management than the local \@Builder. It is applicable to scenarios where the parent-child relationships of components need to be maintained in custom build functions and state management synchronization needs to be kept.

For details about the development guide, see [\@LocalBuilder Decorator: Maintaining Component Relationships](../../../ui/state-management/arkts-localBuilder.md).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-unnamed-declare const LocalBuilder: MethodDecorator--><!--Device-unnamed-declare const LocalBuilder: MethodDecorator-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
