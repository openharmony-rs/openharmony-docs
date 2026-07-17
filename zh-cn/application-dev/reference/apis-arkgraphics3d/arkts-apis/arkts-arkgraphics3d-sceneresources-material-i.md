# Material

材质资源.

**继承/实现关系：** Material extends [SceneResource](arkts-arkgraphics3d-sceneresources-sceneresource-i.md)

**起始版本：** 12

<!--Device-unnamed-export interface Material extends SceneResource--><!--Device-unnamed-export interface Material extends SceneResource-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## alphaCutoff

```TypeScript
alphaCutoff?: number
```

透明度截止值[0,1]. Enabled if < 1.

**类型：** number

**起始版本：** 20

<!--Device-Material-alphaCutoff?: double--><!--Device-Material-alphaCutoff?: double-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## blend

```TypeScript
blend?: Blend
```

控制是否启用混合

**类型：** Blend

**默认值：** undefined, which means that blending is disabled.

**起始版本：** 20

<!--Device-Material-blend?: Blend--><!--Device-Material-blend?: Blend-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## cullMode

```TypeScript
cullMode?: CullMode
```

剔除模式.

**类型：** CullMode

**起始版本：** 20

<!--Device-Material-cullMode?: CullMode--><!--Device-Material-cullMode?: CullMode-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## materialType

```TypeScript
readonly materialType: MaterialType
```

材质资源类型.

**类型：** MaterialType

**起始版本：** 12

<!--Device-Material-readonly materialType: MaterialType--><!--Device-Material-readonly materialType: MaterialType-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## polygonMode

```TypeScript
polygonMode?: PolygonMode
```

材质的多边形模式

**类型：** PolygonMode

**默认值：** PolygonMode.FILL 填充多边形模式

**起始版本：** 23

<!--Device-Material-polygonMode?: PolygonMode--><!--Device-Material-polygonMode?: PolygonMode-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## renderSort

```TypeScript
renderSort?: RenderSort
```

层的渲染排序优先级.

**类型：** RenderSort

**起始版本：** 20

<!--Device-Material-renderSort?: RenderSort--><!--Device-Material-renderSort?: RenderSort-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## shadowReceiver

```TypeScript
shadowReceiver?: boolean
```

定义材质是否可以接收阴影.

**类型：** boolean

**起始版本：** 20

<!--Device-Material-shadowReceiver?: boolean--><!--Device-Material-shadowReceiver?: boolean-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

