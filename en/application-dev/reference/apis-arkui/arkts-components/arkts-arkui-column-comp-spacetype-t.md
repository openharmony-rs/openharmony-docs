# SpaceType

```TypeScript
declare type SpaceType = string | number | Resource
```

Describes the supported data types for the **space** parameter in the constructors of the **Column** component. The type is a union of the following types.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

| Type | Description |
| --- | --- |
| string | The value type is string, and the value must be a string that can be converted to a non- negative number. If a negative number or a string that cannot be converted is set, the default value **0** is used. |
| number | The value type is number, and the value must be greater than or equal to 0. If a negative number or invalid value is set, the default value **0** is used. |
| [Resource](../arkts-apis/arkts-arkui-resource-t.md) | The value type is a resource reference type. It can take values from system resources or application resources. |
