# RichEditorLayoutStyle

```TypeScript
interface RichEditorLayoutStyle
```

Defines image layout information.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderRadius

```TypeScript
borderRadius?: Dimension | BorderRadiuses
```

Border radius type, used to describe the border radius of a component.

Default value: the border radius is 0.

When the parameter is of the Dimension type, setting it in Percentage form is not supported.

**Type:** [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) &#124; [BorderRadiuses](../arkts-apis/arkts-arkui-borderradiuses-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## margin

```TypeScript
margin?: Dimension | Margin
```

Margin type, used to describe the margins of a component in different directions.

Default value: the margins in all four directions are 0.

When the parameter is of the Dimension type, the margins in all four directions take effect simultaneously.

**Type:** [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) &#124; [Margin](../arkts-apis/arkts-arkui-margin-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
