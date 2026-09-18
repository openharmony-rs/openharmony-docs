# Component3D properties/events

@extends CommonMethod&lt;Component3DAttribute&gt;

**Inheritance/Implementation:** Component3DAttribute extends CommonMethod<Component3DAttribute>

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

## customRender

```TypeScript
customRender(uri: ResourceStr, selfRenderUpdate: boolean)
```

Set render pipeline of 3D scene render.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUi.Graphics3D

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | Yes | The path of Render pipeline config file |
| selfRenderUpdate | boolean | Yes | Trigger rendering every frame |

## environment

```TypeScript
environment(uri: ResourceStr)
```

Load 3D model environment resource.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUi.Graphics3D

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | Yes | The path of 3D environment resource |

## renderHeight

```TypeScript
renderHeight(value: Dimension)
```

Set render height resolution.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUi.Graphics3D

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) | Yes | Height of gpu render target, target would upscale or downscale to view's height. |

## renderWidth

```TypeScript
renderWidth(value: Dimension)
```

Set render width resolution.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUi.Graphics3D

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) | Yes | Width of gpu render target, target would upscale or downscale to view's width. |

## shader

```TypeScript
shader(uri: ResourceStr)
```

Load shader uri.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUi.Graphics3D

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | Yes | The path of custom shader |

## shaderImageTexture

```TypeScript
shaderImageTexture(uri: ResourceStr)
```

Load shader texture uri.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUi.Graphics3D

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | Yes | The path of texture used by shader |

## shaderInputBuffer

```TypeScript
shaderInputBuffer(buffer: Array<number>)
```

Buffer input for shader animation

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUi.Graphics3D

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| buffer | Array&lt;number&gt; | Yes | The uniform buffer of shader input |
