# Length

```TypeScript
declare type Length = string | number | Resource
```

Defines a size unit.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

| Type | Description |
| --- | --- |
| string | String type. Specify the length [unit](../arkts-components/arkts-arkui-common-comp.md#common) explicitly, for example, **'10px'**, or provide the length in percentage, for example, **'100%'**. <br>**NOTE:** <br>If the unit is not specified, the default unit vp is used, in which case **'10'** is equivalent to 10 vp. |
| number | Number type. The default unit is vp. |
| [Resource](arkts-arkui-resource-t.md) | Size referenced from system or app resources. |
