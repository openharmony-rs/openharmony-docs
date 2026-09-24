# TextMetrics

```TypeScript
declare interface TextMetrics
```

Size information of the text.

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## actualBoundingBoxAscent

```TypeScript
readonly actualBoundingBoxAscent: number
```

Distance from the horizontal line specified by the [CanvasRenderingContext2D.textBaseline](arkts-arkui-canvas-comp-canvastextbaseline-t.md) attribute to the top of the bounding rectangle used to render the text. Read-only.

**Type:** number

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## actualBoundingBoxDescent

```TypeScript
readonly actualBoundingBoxDescent: number
```

Distance from the horizontal line specified by the [CanvasRenderingContext2D.textBaseline](arkts-arkui-canvas-comp-canvastextbaseline-t.md) attribute to the bottom of the bounding rectangle used to render the text. Read-only.

**Type:** number

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## actualBoundingBoxLeft

```TypeScript
readonly actualBoundingBoxLeft: number
```

Distance parallel to the baseline from the alignment point determined by the [CanvasRenderingContext2D.textAlign](arkts-arkui-canvas-comp-canvastextalign-t.md) attribute to the left side of the bounding rectangle of the text. Read-only.

**Type:** number

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## actualBoundingBoxRight

```TypeScript
readonly actualBoundingBoxRight: number
```

Distance parallel to the baseline from the alignment point determined by the [CanvasRenderingContext2D.textAlign](arkts-arkui-canvas-comp-canvastextalign-t.md) attribute to the right side of the bounding rectangle of the text. Read-only.

**Type:** number

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## alphabeticBaseline

```TypeScript
readonly alphabeticBaseline: number
```

Distance from the horizontal line specified by the [CanvasRenderingContext2D.textBaseline](arkts-arkui-canvas-comp-canvastextbaseline-t.md) attribute to the alphabetic baseline of the line box. Read-only.

**Type:** number

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## emHeightAscent

```TypeScript
readonly emHeightAscent: number
```

Distance from the horizontal line specified by the [CanvasRenderingContext2D.textBaseline](arkts-arkui-canvas-comp-canvastextbaseline-t.md) attribute to the top of the em square in the line box. Read-only.

**Type:** number

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## emHeightDescent

```TypeScript
readonly emHeightDescent: number
```

Distance from the horizontal line specified by the [CanvasRenderingContext2D.textBaseline](arkts-arkui-canvas-comp-canvastextbaseline-t.md) attribute to the bottom of the em square in the line box. Read-only.

**Type:** number

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontBoundingBoxAscent

```TypeScript
readonly fontBoundingBoxAscent: number
```

Distance from the horizontal line specified by the [CanvasRenderingContext2D.textBaseline](arkts-arkui-canvas-comp-canvastextbaseline-t.md) attribute to the top of the bounding rectangle of all the fonts used to render the text. Read-only.

**Type:** number

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontBoundingBoxDescent

```TypeScript
readonly fontBoundingBoxDescent: number
```

Distance from the horizontal line specified by the [CanvasRenderingContext2D.textBaseline](arkts-arkui-canvas-comp-canvastextbaseline-t.md) attribute to the bottom of the bounding rectangle of all the fonts used to render the text. Read-only.

**Type:** number

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## hangingBaseline

```TypeScript
readonly hangingBaseline: number
```

Distance from the horizontal line specified by the [CanvasRenderingContext2D.textBaseline](arkts-arkui-canvas-comp-canvastextbaseline-t.md) attribute to the hanging baseline of the line box. Read-only.

**Type:** number

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## height

```TypeScript
readonly height: number
```

Height of the text. Read-only.

Default unit: vp.

If the unit mode of the **CanvasRenderingContext2D** object is set to px, the unit is px.

**Type:** number

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ideographicBaseline

```TypeScript
readonly ideographicBaseline: number
```

Distance from the horizontal line specified by the [CanvasRenderingContext2D.textBaseline](arkts-arkui-canvas-comp-canvastextbaseline-t.md) attribute to the ideographic baseline of the line box. Read-only.

**Type:** number

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
readonly width: number
```

Width of the text. Read-only.

Default unit: vp.

If the unit mode of the **CanvasRenderingContext2D** object is set to px, the unit is px.

**Type:** number

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
