# EnvDecorator

```TypeScript
declare type EnvDecorator = (value: SystemProperties) => PropertyDecorator
```

Defines the **EnvDecorator** property decorator type.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-unnamed-declare type EnvDecorator = (value: SystemProperties) => PropertyDecorator--><!--Device-unnamed-declare type EnvDecorator = (value: SystemProperties) => PropertyDecorator-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [SystemProperties](arkts-arkui-common-comp-systemproperties-e.md) | Yes | Environment variable attribute name, used to specify the system environment variable to obtain. |

**Return value:**

| Type | Description |
| --- | --- |
| [PropertyDecorator](../../apis-default/arkts-apis/arkts-propertydecorator-t.md) | Property decorator. You do not need to pay attention to this return value. |
