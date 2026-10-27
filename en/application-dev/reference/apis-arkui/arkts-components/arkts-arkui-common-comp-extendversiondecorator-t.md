# ExtendVersionDecorator

```TypeScript
declare type ExtendVersionDecorator = (value: any, versionCondition: VersionCondition) => MethodDecorator
```

Define Extend Decorator type with version control.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.1.0.

<!--Device-unnamed-declare type ExtendVersionDecorator = (value: any, versionCondition: VersionCondition) => MethodDecorator--><!--Device-unnamed-declare type ExtendVersionDecorator = (value: any, versionCondition: VersionCondition) => MethodDecorator-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | any | Yes |  |
| versionCondition | [VersionCondition](arkts-arkui-common-comp-versioncondition-i.md) | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| [MethodDecorator](../../apis-default/arkts-apis/arkts-methoddecorator-t.md) | Extend decorator |
