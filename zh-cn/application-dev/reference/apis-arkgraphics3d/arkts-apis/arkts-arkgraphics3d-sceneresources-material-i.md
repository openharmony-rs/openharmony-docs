# Material

材质类型，继承自SceneResource。@extends SceneResource @interface Material

**继承/实现关系：** Material extends [SceneResource](arkts-arkgraphics3d-sceneresources-sceneresource-i.md)

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

## alphaCutoff

```TypeScript
alphaCutoff?: number
```

透明通道阈值，如果像素的alpha值等于或高于此阈值，则渲染该像素；如果低于此阈值，则不会渲染该像素。 设置值小于1时，则开启该模式，取值范围为[0, 1]，默认值为1。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.ArkUi.Graphics3D

## blend

```TypeScript
blend?: Blend
```

材质的透明效果设置，默认值为undefined，即禁用材质的透明属性。

**类型：** [Blend](arkts-arkgraphics3d-sceneresources-blend-i.md)

**默认值：** undefined

**起始版本：** 20

**系统能力：** SystemCapability.ArkUi.Graphics3D

## cullMode

```TypeScript
cullMode?: CullMode
```

当前材质的剔除模式设置，用于控制是否剔除背面几何面片，默认值为BACK。

**类型：** [CullMode](arkts-arkgraphics3d-sceneresources-cullmode-e.md)

**起始版本：** 20

**系统能力：** SystemCapability.ArkUi.Graphics3D

## materialType

```TypeScript
readonly materialType: MaterialType
```

材质类型。

**类型：** [MaterialType](arkts-arkgraphics3d-sceneresources-materialtype-e.md)

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

## polygonMode

```TypeScript
polygonMode?: PolygonMode
```

模型的多边形绘制模式，默认值为FILL。

**类型：** [PolygonMode](arkts-arkgraphics3d-sceneresources-polygonmode-e.md)

**默认值：** PolygonMode.FILL

**起始版本：** 23

**系统能力：** SystemCapability.ArkUi.Graphics3D

## renderSort

```TypeScript
renderSort?: RenderSort
```

渲染排序设置，用于控制材质在渲染管线中的渲染顺序，渲染图层id默认值为32，同一图层内的渲染顺序默认值为0。

**类型：** [RenderSort](arkts-arkgraphics3d-sceneresources-rendersort-i.md)

**起始版本：** 20

**系统能力：** SystemCapability.ArkUi.Graphics3D

## shadowReceiver

```TypeScript
shadowReceiver?: boolean
```

材质是否接收阴影。true表示该材质接收阴影，false表示不接收，默认值为false。

**类型：** boolean

**起始版本：** 20

**系统能力：** SystemCapability.ArkUi.Graphics3D
