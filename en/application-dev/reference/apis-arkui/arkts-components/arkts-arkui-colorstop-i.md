# ColorStop

Describes the gradient color stop.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color: ResourceColor
```

Color value at the gradient color stop.

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset: Length
```

Gradient color stop (proportion value between 0 and 1). A value less than 0 evaluates to the value **0**. A value greater than 1 evaluates to the value **1**.

**NOTE:** 

If the value is a string that represents a number, it will be converted to a number.

For example, **'10vp'** is converted to 10, and **'10%'** is converted to 0.1.

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
