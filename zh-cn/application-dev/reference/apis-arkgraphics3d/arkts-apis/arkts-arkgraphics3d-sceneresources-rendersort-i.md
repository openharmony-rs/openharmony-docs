# RenderSort

定义材质物体的渲染顺序，控制不同物体在渲染管线中的绘制先后。

**起始版本：** 23

<!--Device-unnamed-export interface RenderSort--><!--Device-unnamed-export interface RenderSort-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## renderSortLayer

```TypeScript
renderSortLayer?: int
```

渲染图层id，数值越小，渲染顺序越靠前。取值范围[0, 63]，默认图层id为32。

**类型：** int

**默认值：** 32

**起始版本：** 23

<!--Device-RenderSort-renderSortLayer?: int--><!--Device-RenderSort-renderSortLayer?: int-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## renderSortLayerOrder

```TypeScript
renderSortLayerOrder?: int
```

同一渲染图层内，不同物体的渲染顺序，数值越小，越先渲染。取值范围[0, 255]，默认值为0。

**类型：** int

**默认值：** 0

**起始版本：** 23

<!--Device-RenderSort-renderSortLayerOrder?: int--><!--Device-RenderSort-renderSortLayerOrder?: int-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

