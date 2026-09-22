# AtlasImage（系统接口）

```TypeScript
interface AtlasImage
```

定义精灵图序列帧动画的图集帧参数。

**起始版本：** 26.0.1

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';
```

## atlasImage

```TypeScript
atlasImage: image.PixelMap
```

精灵图集图片。通过image模块创建，为PixelMap实例。

**类型：** [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## cols

```TypeScript
cols: number
```

精灵图集的列数。取值范围为[1, totalFrame]，超出范围的值将在内部被截断。

> **说明：** 
> 
> cols * (frameWidth + 2 * padding) 不得超过图集图片的宽度。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## frameHeight

```TypeScript
frameHeight: number
```

单帧的高度。取值范围为[1, 8192]，超出范围的值将在内部被截断。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## frameIndex

```TypeScript
frameIndex: number
```

当前帧在图集中的索引。取值范围为[0, totalFrame - 1]，超出范围的值将在内部被截断。

> **说明：** 
> 
> 该字段可通过[animateTo](../../apis-arkui/arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#animateto)进行动画驱动。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## frameWidth

```TypeScript
frameWidth: number
```

单帧的宽度。取值范围为[1, 8192]，超出范围的值将在内部被截断。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## mode

```TypeScript
mode: AtlasInterpolationMode
```

帧动画的插值模式。NONE(0) = 无插值，每帧独立显示；FRAME_BLEND(1) = 帧间插值，相邻帧之间平滑过渡。

**类型：** [AtlasInterpolationMode](arkts-arkgraphics2d-drawing-atlasinterpolationmode-e-sys.md)

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## padding

```TypeScript
padding: number
```

帧之间的间距，用于防止帧边界处的纹理渗透。取值范围为[0, 64]，超出范围的值将在内部被截断。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## rows

```TypeScript
rows: number
```

精灵图集的行数。取值范围为[1, totalFrame]，超出范围的值将在内部被截断。

> **说明：** 
> 
> rows * (frameHeight + 2 * padding) 不得超过图集图片的高度。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## totalFrame

```TypeScript
totalFrame: number
```

图集中的总帧数。取值范围为[1, rows * cols]，超出范围的值将在内部被截断。

> **说明：** 
> 
> 不得超过 rows * cols。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。
