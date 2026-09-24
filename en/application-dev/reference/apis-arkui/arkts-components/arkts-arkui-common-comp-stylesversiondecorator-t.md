# StylesVersionDecorator

```TypeScript
declare type StylesVersionDecorator = (versionCondition: VersionCondition) => MethodDecorator
```

Define Styles Decorator type with version control.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.2.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| versionCondition | [VersionCondition](arkts-arkui-common-comp-versioncondition-i.md) | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| [MethodDecorator](../../apis-default/arkts-apis/arkts-methoddecorator-t.md) | Styles decorator |
