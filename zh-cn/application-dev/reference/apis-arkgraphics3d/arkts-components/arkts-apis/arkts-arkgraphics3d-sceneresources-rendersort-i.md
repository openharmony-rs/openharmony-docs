# RenderSort

定义材质物体的渲染顺序，控制不同物体在渲染管线中的绘制先后。

@interface RenderSort

**起始版本：** 20

**系统能力：** SystemCapability.ArkUi.Graphics3D

## renderSortLayer

```TypeScript
renderSortLayer?: number
```

渲染图层id，数值越小，渲染顺序越靠前。取值范围[0, 63]，默认图层id为32。

**类型：** number

**默认值：** 32

**起始版本：** 20

**系统能力：** SystemCapability.ArkUi.Graphics3D

## renderSortLayerOrder

```TypeScript
renderSortLayerOrder?: number
```

同一渲染图层内，不同物体的渲染顺序，数值越小，越先渲染。取值范围[0, 255]，默认值为0。

**类型：** number

**默认值：** 0

**起始版本：** 20

**系统能力：** SystemCapability.ArkUi.Graphics3D
