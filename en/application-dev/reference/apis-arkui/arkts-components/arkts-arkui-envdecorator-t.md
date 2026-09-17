# EnvDecorator

```TypeScript
declare type EnvDecorator = (value: SystemProperties) => PropertyDecorator
```

Define Env Decorator type

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [SystemProperties](arkts-arkui-systemproperties-e.md) | Yes | key value input by the user |

**Return value:**

| Type | Description |
| --- | --- |
| [PropertyDecorator](../../apis-default/arkts-apis/arkts-propertydecorator-t.md) | Env decorator |
