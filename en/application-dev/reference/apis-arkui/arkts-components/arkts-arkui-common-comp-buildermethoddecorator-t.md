# BuilderMethodDecorator

```TypeScript
declare type BuilderMethodDecorator = (value: BuilderDecoratorConfig) => MethodDecorator
```

Define Builder Decorator type with config.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.1.0.

<!--Device-unnamed-declare type BuilderMethodDecorator = (value: BuilderDecoratorConfig) => MethodDecorator--><!--Device-unnamed-declare type BuilderMethodDecorator = (value: BuilderDecoratorConfig) => MethodDecorator-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [BuilderDecoratorConfig](arkts-arkui-common-comp-builderdecoratorconfig-i.md) | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| [MethodDecorator](../../apis-default/arkts-apis/arkts-methoddecorator-t.md) | Method Decorator |
