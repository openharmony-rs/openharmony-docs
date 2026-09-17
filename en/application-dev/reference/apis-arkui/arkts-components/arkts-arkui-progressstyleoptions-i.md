# ProgressStyleOptions

Defines the progress bar style options.

Inherits from [CommonProgressStyleOptions](arkts-arkui-commonprogressstyleoptions-i.md).

**Inheritance/Implementation:** ProgressStyleOptions extends [CommonProgressStyleOptions](arkts-arkui-commonprogressstyleoptions-i.md)

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## scaleCount

```TypeScript
scaleCount?: number
```

Number of divisions on the ring-style process indicator.

Default value: **120**

Value range: [2, min(width, height)/scaleWidth/2/π]. If the value is outside this range, the progress indicator is displayed in the indeterminate ring style. By default, the minimum width and height are 77 vp.

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## scaleWidth

```TypeScript
scaleWidth?: Length
```

Scale width of the ring-style progress indicator. Percentage values are not supported. If the scale width is greater than the stroke width of the progress indicator, the default scale width is used.

Default value: **2.0vp**

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## strokeWidth

```TypeScript
strokeWidth?: Length
```

Stroke width of the progress indicator. Percentage values are not supported.

Default value: **4.0vp**

If the value is out of the range, the default value is used.

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
