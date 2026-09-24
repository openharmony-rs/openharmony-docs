# PointLightStyle (System API)

```TypeScript
declare interface PointLightStyle
```

You apply a point light style by setting the light source that emits illumination and the components to be illuminated.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## bloom

```TypeScript
bloom?: number
```

Luminous intensity of the component. The recommended value range is 0-1.

Default value: **0**

**Type:** number

**Default:** 0

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## illuminated

```TypeScript
illuminated?: IlluminatedType
```

Whether the current component can be illuminated by the light source and the illuminated type.

Default value: **IlluminatedType.NONE**

**Type:** [IlluminatedType](../arkts-apis/arkts-arkui-illuminatedtype-e-sys.md)

**Default:** IlluminatedType.NONE

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## lightSource

```TypeScript
lightSource?: LightSource
```

Light source. The light source affects the surrounding components that are marked as illuminable and creates light effects on those components.

Default value: none

**Type:** [LightSource](arkts-arkui-common-comp-lightsource-i-sys.md)

**Default:** undefined

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
