# CommonMethod

CommonMethod.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## advancedBlendMode

```TypeScript
advancedBlendMode(effect: BlendMode | Blender, type?: BlendApplyType): T
```

Defines how the component's content (including the content of it child components) is blended with the existing content on the canvas (possibly offscreen canvas) below. This API cannot be used with [blendMode](arkts-arkui-commonmethod-c.md#blendmode).

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Widget capability:** This API can be used in ArkTS widgets since API version 13.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| effect | [BlendMode](arkts-arkui-blendmode-e.md) &#124; [Blender](arkts-arkui-blender-t-sys.md) | Yes | Blend mode or blender type, depending on the parameter type.<br>When the parameter type is **BlendMode**, it indicates the blend mode.<br>Default value: **BlendMode.NONE**<br>When the parameter type is **Blender**, it indicates the blender type, used to describe the blending effect.<br>A **Blender** instance must be created using methods, for example, [uiEffect.createBrightnessBlender](../../../reference/apis-arkgraphics2d/js-apis-uiEffect-sys.md#uieffectcreatebrightnessblender), from the **uiEffect** module. Using a custom object as a parameter will not take effect. |
| type | [BlendApplyType](arkts-arkui-blendapplytype-e.md) | No | Whether the blend mode is implemented offscreen.<br>Default value: **BlendApplyType.FAST**<br>**NOTE:** <br>1. When this parameter is set to **BlendApplyType.FAST**, the blend mode is not implemented offscreen.<br>2. When this parameter is set to **BlendApplyType.OFFSCREEN**, an offscreen canvas matching the size of the current component is created. The content of the current component (including its child components) is then drawn onto the offscreen canvas, and blended with the existing content on the underlying canvas using the specified blend mode.<br>3. For text components, this API does not apply to emoji expressions when not offscreen.<br>4. Compared with **BlendApplyType.OFFSCREEN**, when this parameter is set to **BlendApplyType.OFFSCREEN_WITH_BACKGROUND**, the system first copies a canvas with a background as the initial background color (the canvas for **BlendApplyType.OFFSCREEN** starts with a transparent background) when creating an offscreen canvas matching the current component's size. The blending operation is then performed on this base. The two modes are identical in all other functional aspects. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## constructor

```TypeScript
constructor()
```

constructor.

**Since:** 9

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## edgeLight

```TypeScript
edgeLight(params: EdgeLightParams | undefined): T
```

Sets the edge light effect for the component.

<p>&lt;strong&gt;NOTE&lt;/strong&gt;: <br>The edge light effect creates a glowing light effect along the component's edges, starting from the specified position and extending along the edge. <br>This effect can enhance the visual appeal and highlight important components. </p>

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| params | [EdgeLightParams](arkts-arkui-edgelightparams-i-sys.md) &#124; undefined | Yes | Edge light effect parameters. Defines the position, length, intensity, color, and thickness of the light effect. If params is undefined, the edge light effect is removed. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## excludeFromRenderGroup

```TypeScript
excludeFromRenderGroup(exclude: boolean | undefined): T
```

Sets whether the current component and its child components are removed from the render group of the ancestor component. If this attribute is used alone, no effect is achieved. It must be used with the [renderGroup](arkts-arkui-commonmethod-c.md#rendergroup) attribute of the ancestor component.

Removing the current component and its children from the render group does not affect the offscreen canvas of the ancestor component, and the cache of the render group is still valid. In this way, the render group cache can be reused. If the display area of the current component occupies only a part of the display area of the render group drawing content, and the display effect of the current component and its children is frequently updated, setting **excludeFromRenderGroup** helps optimize the drawing performance.

If this attribute is not set, the current component and its children are not removed from the render group of the ancestor component by default.

> **NOTE:** 
> 
> The drawing content of the component with **excludeFromRenderGroup** set to **true** and its children cannot the
> component's own boundary range. Otherwise, the displayed content may be clipped. For example, if the child
> component exceeds the boundary range of the current component due to attributes such as
> [translate](arkts-arkui-commonmethod-c.md#translate) or
> [scale](arkts-arkui-commonmethod-c.md#scale), or the drawing content extend beyond its boundaries
> because the current component has attributes such as
> [shadow](arkts-arkui-commonmethod-c.md#shadow) and
> [pixelStretchEffect](arkts-arkui-commonmethod-c.md#pixelstretcheffect), the displayed
> content may be clipped. In such scenarios, **excludeFromRenderGroup** should not be set to **true**.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| exclude | boolean &#124; undefined | Yes | Whether to remove the current component and its child components from the render group of the ancestor component.<br>**true**: yes. **false**: no.<br>If **exclude** is set to **undefined**, the value **false** is used. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## markLayeredRender

```TypeScript
markLayeredRender(value: boolean | undefined): T
```

Marks the node as an independent render layer. Once marked, the component and its child components are rendered independently, so that when a popup is displayed above it, the component itself does not need to be rendered again.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean &#124; undefined | Yes | Whether to mark the node as an independent render layer. The value **true** means to mark the node as an independent render layer, and **false** or **undefined** means to cancel the mark. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## spatialEffect

```TypeScript
spatialEffect(params: SpatialEffectParams | undefined): T
```

Applies a spatial effect to component.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| params | [SpatialEffectParams](arkts-arkui-spatialeffectparams-i-sys.md) &#124; undefined | Yes | Spatial effect parameters. |

**Return value:**

| Type | Description |
| --- | --- |
| T |  |

## useUnionEffect

```TypeScript
useUnionEffect(value: boolean | undefined): T
```

Specify whether the current component participates in the fusion effect of the ancestor component UnionEffectContainer

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean &#124; undefined | Yes | Whether the component participates in the fusion effect of the ancestor component **UnionEffectContainer**.<br>The value **true** means that the component participates in the fusion effect of the ancestor component **UnionEffectContainer**, and **false** means the opposite. <br>Default value: **false**. Undefined means to default value. |

**Return value:**

| Type | Description |
| --- | --- |
| T | return the component attribute. |

## useUnionEffect

```TypeScript
useUnionEffect(value: boolean | undefined, options?: GravityCenterOptions): T
```

Specify whether the current component participates in the fusion effect of the ancestor component UnionEffectContainer

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean &#124; undefined | Yes | Whether the component participates in the fusion effect of the ancestor component **UnionEffectContainer**. The value **true** means that the component participates in the fusion effect of the ancestor component **UnionEffectContainer**, and **false** means the opposite. |
| options | [GravityCenterOptions](arkts-arkui-gravitycenteroptions-i-sys.md) | No | Gravitational center parameter. GRAVITY_UNION. |

**Return value:**

| Type | Description |
| --- | --- |
| T | return the component attribute. |
