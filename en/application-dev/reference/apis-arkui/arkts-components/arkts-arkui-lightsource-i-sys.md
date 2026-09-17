# LightSource (System API)

Each component allows for one light source.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## color

```TypeScript
color?: ResourceColor
```

Light source color.

Default value: **Color.White**

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## intensity

```TypeScript
intensity: number
```

Intensity of the light source. The recommended value range is 0-1. When the intensity is **0**, the light source does not emit light.

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## positionX

```TypeScript
positionX: Dimension
```

X-coordinate of the light source relative to the current component.

**Type:** [Dimension](../arkts-apis/arkts-arkui-dimension-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## positionY

```TypeScript
positionY: Dimension
```

Y-coordinate of the light source relative to the current component.

**Type:** [Dimension](../arkts-apis/arkts-arkui-dimension-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## positionZ

```TypeScript
positionZ: Dimension
```

Height of the light source. The higher the light source, the broader the light distribution.

**Type:** [Dimension](../arkts-apis/arkts-arkui-dimension-t.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
