# ResponseRegion

Defines a touch target consisting of an input tool type, touch position, and size.

> **NOTE:** 
> 
> - When the parent component has [clip](arkts-arkui-commonmethod-c.md#clip) set to **true**, child component interaction is affected by the parent component's response region. Children outside the parent component's response region won't respond to gestures or events.
> 
> - If the input tool type, touch position, and size are not configured for a touch target, default values are used.
> 
> - Positive calculation results for x and y represent shifts to the right and down, respectively. Negative calculation results represent shifts to the left and up, respectively.
> 
> - If the width and height are of the string type, the string must be in lowercase. Dynamic calculation with
> **calc()** is supported. The format of the input string for **calc()** is Width/Height scaling ratio ± Width/Height
> increment, where the scaling ratio is a percentage and the increment unit is px or vp. For example, in
> **calc(80% + 10vp)**, **80%** is the width/height scaling ratio, and **10vp** is the width/height increment. If the
> width and height are of the **LengthMetrics** type and the unit is percent, the width and height are calculated
> relative to the component's own width and height. **percent(1)** indicates 100%. If the calculation result is a
> negative value, the default value is used.

**Since:** 22

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## height

```TypeScript
height?: LengthMetrics | string
```

Height of the touch target.

Default value: **LengthMetrics.percent(1)**

**Type:** [LengthMetrics](../arkts-apis/arkts-arkui-lengthmetrics-t.md) &#124; string

**Default:** LengthMetrics.percent(1)

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## tool

```TypeScript
tool?: ResponseRegionSupportedTool
```

Type of the input tool applicable to the touch target.

Default value: **ResponseRegionSupportedTool.ALL**

**Type:** [ResponseRegionSupportedTool](../arkts-apis/arkts-arkui-responseregionsupportedtool-e.md)

**Default:** ResponseRegionSupportedTool.ALL

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: LengthMetrics | string
```

Width of the touch target.

Default value: **LengthMetrics.percent(1)**

**Type:** [LengthMetrics](../arkts-apis/arkts-arkui-lengthmetrics-t.md) &#124; string

**Default:** LengthMetrics.percent(1)

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## x

```TypeScript
x?: LengthMetrics
```

X coordinate of the touch point relative to the upper left corner of the component.

Default value: **LengthMetrics.vp(0)**

**Type:** [LengthMetrics](../arkts-apis/arkts-arkui-lengthmetrics-t.md)

**Default:** LengthMetrics.vp(0)

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## y

```TypeScript
y?: LengthMetrics
```

Y coordinate of the touch point relative to the upper left corner of the component.

Default value: **LengthMetrics.vp(0)**

**Type:** [LengthMetrics](../arkts-apis/arkts-arkui-lengthmetrics-t.md)

**Default:** LengthMetrics.vp(0)

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
