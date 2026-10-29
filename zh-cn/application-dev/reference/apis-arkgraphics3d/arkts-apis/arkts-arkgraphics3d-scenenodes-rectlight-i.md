# RectLight

```TypeScript
export interface RectLight extends Light
```

矩形区域光类型，继承自[Light](arkts-arkgraphics3d-scenenodes-light-i.md)。

矩形光源从矩形区域发射光，模拟柔和的区域照明效果，强度随着距离的增加而衰减。

> **注意：**
> 
> 矩形面光源不支持阴影投射，设置[Light](arkts-arkgraphics3d-scenenodes-light-i.md)的shadowEnabled属性不生效。此外，矩形面光源功耗较高、性能开销较大，建议优先使用[DirectionalLight](arkts-arkgraphics3d-scenenodes-directionallight-i.md)等其他光源类型近似想要的渲染效果。

**继承/实现关系：** RectLight extends [Light](arkts-arkgraphics3d-scenenodes-light-i.md)

**起始版本：** 26.1.0

<!--Device-unnamed-export interface RectLight extends Light--><!--Device-unnamed-export interface RectLight extends Light-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## height

```TypeScript
height?: number
```

矩形发光面的高度。单位为世界坐标系下的场景单位（比如cm、m、km等），取值大于0，若未设置，默认为1。

**类型：** number

**默认值：** 1.0

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RectLight-height?: double--><!--Device-RectLight-height?: double-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## twoSided

```TypeScript
twoSided?: boolean
```

矩形光源是否从矩形的两侧发光。若未设置，默认为false。

**类型：** boolean

**默认值：** false

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RectLight-twoSided?: boolean--><!--Device-RectLight-twoSided?: boolean-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## width

```TypeScript
width?: number
```

矩形发光面的宽度。单位为世界坐标系下的场景单位（比如cm、m、km等），取值大于0，若未设置，默认为1。

**类型：** number

**默认值：** 1.0

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RectLight-width?: double--><!--Device-RectLight-width?: double-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D
