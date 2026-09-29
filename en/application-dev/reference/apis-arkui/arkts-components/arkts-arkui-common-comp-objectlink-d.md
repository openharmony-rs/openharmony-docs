# @ObjectLink

```TypeScript
declare const ObjectLink: PropertyDecorator
```

**\@ObjectLink** is used in [state management V1](../../../ui/state-management/arkts-state-management-overview.md) to receive instances of classes decorated with [@Observed](arkts-arkui-common-comp-observed-d.md#observed) and establish two-way data binding with the data source in the parent component. It is applicable to scenarios where nested class properties are independently observed and listened to in child components to trigger UI updates.

For details, see [@Observed and @ObjectLink Decorators: Observing Property Changes in Nested Class Objects](../../../ui/state-management/arkts-observed-and-objectlink.md).

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-unnamed-declare const ObjectLink: PropertyDecorator--><!--Device-unnamed-declare const ObjectLink: PropertyDecorator-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
