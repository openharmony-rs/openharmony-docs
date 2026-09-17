# EdgeLightParams (System API)

Defines the parameters of the edge light effect.

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## color

```TypeScript
color?: ResourceColor
```

The color of the light effect. <br>If not specified, the default color is white (#FFFFFF).

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Default:** #FFFFFF

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## intensity

```TypeScript
intensity?: number
```

The luminous intensity of the Edge Streamer effect. <br>Valid range: [0.0, 1.0].Default value is 1. <br>Value 0.0 means the light effect is completely invisible. <br>Value 1.0 means the light effect is at maximum brightness. <br>Values exceeding 1.0 will be clamped to 1.0. <br>Negative values are treated as 0.0.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## length

```TypeScript
length: Length
```

Projection length of the edge streamer along the flow direction. <br>Negative values are treated as 0.

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## position

```TypeScript
position: EdgeLightPosition
```

The location of the edge light effect.

**Type:** [EdgeLightPosition](../arkts-apis/arkts-arkui-edgelightposition-e-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## thickness

```TypeScript
thickness?: Length
```

The thickness (width) of the light effect line. <br>Negative values are treated as 0. <br>If not specified, the default value is 0vp.

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Default:** 0vp

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
