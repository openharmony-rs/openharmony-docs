# ColorMetricsStop

```TypeScript
declare interface ColorMetricsStop
```

Describes the breakpoint of the gradient color.

**Since:** 23

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color: ColorMetrics
```

Color value of the linear gradient color breakpoint.

**Type:** ColorMetrics

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset: Length
```

Value of the linear gradient color stop. The value is a proportion ranging from 0 to 1. If a value less than 0 is passed, the value is set to **0**. If a value greater than 1 is passed, the value is set to **1**.

**NOTE:** 

If the value is a string that represents a number, it will be converted to a number. For example, **'10vp'** is converted to **10**, and **'10%'** is converted to **0.1**.

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
