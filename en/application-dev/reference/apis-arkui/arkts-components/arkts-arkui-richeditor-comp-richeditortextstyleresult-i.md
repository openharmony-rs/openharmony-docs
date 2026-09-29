# RichEditorTextStyleResult

```TypeScript
declare interface RichEditorTextStyleResult
```

Provides the text span style information returned by the backend.

While **fontWeight** in **RichEditorTextStyle** sets the font weight,

**fontWeight** in **RichEditorTextStyleResult** returns the set font weight after conversion to digits.

**Since:** 10

<!--Device-unnamed-declare interface RichEditorTextStyleResult--><!--Device-unnamed-declare interface RichEditorTextStyleResult-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## decoration

```TypeScript
decoration: DecorationStyleResult
```

Text decoration.

**Type:** [DecorationStyleResult](../arkts-apis/arkts-arkui-decorationstyleresult-i.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-RichEditorTextStyleResult-decoration: DecorationStyleResult--><!--Device-RichEditorTextStyleResult-decoration: DecorationStyleResult-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontColor

```TypeScript
fontColor: ResourceColor
```

Font color.

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-RichEditorTextStyleResult-fontColor: ResourceColor--><!--Device-RichEditorTextStyleResult-fontColor: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontFamily

```TypeScript
fontFamily: string
```

Font family.

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-RichEditorTextStyleResult-fontFamily: string--><!--Device-RichEditorTextStyleResult-fontFamily: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontFeature

```TypeScript
fontFeature?: string
```

Font feature.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-RichEditorTextStyleResult-fontFeature?: string--><!--Device-RichEditorTextStyleResult-fontFeature?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize: number
```

Font size. The default unit is fp.

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-RichEditorTextStyleResult-fontSize: number--><!--Device-RichEditorTextStyleResult-fontSize: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontStyle

```TypeScript
fontStyle: FontStyle
```

Font style.

**Type:** [FontStyle](../arkts-apis/arkts-arkui-fontstyle-e.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-RichEditorTextStyleResult-fontStyle: FontStyle--><!--Device-RichEditorTextStyleResult-fontStyle: FontStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontWeight

```TypeScript
fontWeight: number
```

Font weight.

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-RichEditorTextStyleResult-fontWeight: number--><!--Device-RichEditorTextStyleResult-fontWeight: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## halfLeading

```TypeScript
halfLeading?: boolean
```

Whether half leading is enabled.

**true**: Half leading is enabled. **false**: Half leading is not enabled.

Default value: **false**

**Type:** boolean

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-RichEditorTextStyleResult-halfLeading?: boolean--><!--Device-RichEditorTextStyleResult-halfLeading?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## letterSpacing

```TypeScript
letterSpacing?: number
```

Letter spacing. The default unit is fp.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-RichEditorTextStyleResult-letterSpacing?: number--><!--Device-RichEditorTextStyleResult-letterSpacing?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## lineHeight

```TypeScript
lineHeight?: number
```

Line height. The default unit is fp.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-RichEditorTextStyleResult-lineHeight?: number--><!--Device-RichEditorTextStyleResult-lineHeight?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## strokeColor

```TypeScript
strokeColor?: ResourceColor
```

Text stroke color.

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-RichEditorTextStyleResult-strokeColor?: ResourceColor--><!--Device-RichEditorTextStyleResult-strokeColor?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## strokeJoinStyle

```TypeScript
strokeJoinStyle?: StrokeJoinStyle
```

Corner style of the text stroke.

Default value: StrokeJoinStyle.MITER_JOIN.

**Type:** [StrokeJoinStyle](../arkts-apis/arkts-arkui-strokejoinstyle-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-RichEditorTextStyleResult-strokeJoinStyle?: StrokeJoinStyle--><!--Device-RichEditorTextStyleResult-strokeJoinStyle?: StrokeJoinStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## strokeWidth

```TypeScript
strokeWidth?: number
```

Text stroke width.

The unit is vp.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-RichEditorTextStyleResult-strokeWidth?: number--><!--Device-RichEditorTextStyleResult-strokeWidth?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textBackgroundStyle

```TypeScript
textBackgroundStyle?: TextBackgroundStyle
```

Text background style.

Default value:

{

color: Color.Transparent,

radius: 0

}

**Type:** [TextBackgroundStyle](arkts-arkui-span-comp-textbackgroundstyle-i.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-RichEditorTextStyleResult-textBackgroundStyle?: TextBackgroundStyle--><!--Device-RichEditorTextStyleResult-textBackgroundStyle?: TextBackgroundStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textShadow

```TypeScript
textShadow?: Array<ShadowOptions>
```

Text shadow.

**NOTE:** 

Only the shadow blur radius, shadow color, and shadow offset can be queried.

**Type:** Array&lt;[ShadowOptions](arkts-arkui-common-comp-shadowoptions-i.md)&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-RichEditorTextStyleResult-textShadow?: Array<ShadowOptions>--><!--Device-RichEditorTextStyleResult-textShadow?: Array<ShadowOptions>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
