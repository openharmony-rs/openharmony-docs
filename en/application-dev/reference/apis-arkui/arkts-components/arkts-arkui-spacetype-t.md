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
| string | Represents a string value. It can take any string value. |
| number | Represents a numeric value. It can take any numerical value. |
| [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Represents a resource reference type. It can take values from system resources or application resources. |
