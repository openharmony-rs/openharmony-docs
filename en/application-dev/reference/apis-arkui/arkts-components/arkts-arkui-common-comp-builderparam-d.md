# @BuilderParam

```TypeScript
declare const BuilderParam: PropertyDecorator
```

**\@BuilderParam** is used to decorate variables that point to [\@Builder](arkts-arkui-common-comp-builder-d.md#builder) functions, enabling a custom component to receive externally passed **\@Builder** functions for custom rendering of UI content. It is suitable for scenarios where the parent component's UI building logic needs to be passed to a child component to achieve dynamic customization of component content.

For details, see the development guide: [\@BuilderParam Decorator: Referencing the @Builder Function](../../../ui/state-management/arkts-builderparam.md).

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-unnamed-declare const BuilderParam: PropertyDecorator--><!--Device-unnamed-declare const BuilderParam: PropertyDecorator-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
