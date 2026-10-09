# @ohos.graphics.drawing (绘制模块)(系统接口)

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->

Drawing模块提供基础的图形绘制能力，包括绘制矩形、圆形、点、直线、自定义Path和字体等。本页面仅包含该模块的系统接口。

> **说明：**
>
> - 本模块首批接口从API version 11开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 页面仅包含本模块的系统接口，其他公开接口参见[@ohos.graphics.drawing (绘制模块)](arkts-apis-graphics-drawing.md)。
> - 本模块使用屏幕物理像素单位px。
> - 本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。

## 导入模块

```ts
import { drawing } from '@kit.ArkGraphics2D';
```

## AtlasInterpolationMode

精灵图集（[Sprite Sheet](../../graphics/graphic-term.md#sprite-sheet精灵图集)）序列帧动画的插值模式枚举。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Graphics.Drawing

| 名称        | 值   | 说明                                                         |
| ----------- | ---- | ------------------------------------------------------------ |
| NONE        | 0    | 无插值。每帧独立显示。 |
| FRAME_BLEND | 1    | 帧间插值。在相邻帧之间进行平滑过渡。 |

## AtlasImage

定义精灵图集（[Sprite Sheet](../../graphics/graphic-term.md#sprite-sheet精灵图集)）序列帧动画的图集帧参数。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Graphics.Drawing

| 名称        | 类型   | 只读 | 可选 | 说明   |
| ----------- | ------ | ---- | ---- | ------ |
| atlasImage  | [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) | 否   | 否   | 精灵图集图片。|
| rows        | number | 否   | 否   | 精灵图集的行数。取值范围为[1, totalFrame]，超出范围的值将在内部被截断。<br>rows * (frameHeight + 2 * padding)不得超过图集图片的高度。|
| cols        | number | 否   | 否   | 精灵图集的列数。取值范围为[1, totalFrame]，超出范围的值将在内部被截断。<br>cols * (frameWidth + 2 * padding)不得超过图集图片的宽度。|
| frameWidth  | number | 否   | 否   | 单帧的宽度，单位为px。取值范围为[1, 8192]，超出范围的值将在内部被截断。|
| frameHeight | number | 否   | 否   | 单帧的高度，单位为px。取值范围为[1, 8192]，超出范围的值将在内部被截断。|
| padding     | number | 否   | 否   | 帧之间的间距，单位为px，用于防止帧边界处的纹理渗透。取值范围为[0, 64]，超出范围的值将在内部被截断。|
| frameIndex  | number | 否   | 否   | 当前帧在图集中的索引。取值范围为[0, totalFrame - 1]，超出范围的值将在内部被截断。<br>该字段可通过[animateTo](../apis-arkui/arkts-apis-uicontext-uicontext.md#animateto)进行动画驱动。|
| totalFrame  | number | 否   | 否   | 图集中的总帧数。取值范围为[1, rows * cols]，超出范围的值将在内部被截断。|
| mode        | [drawing.AtlasInterpolationMode](#atlasinterpolationmode) | 否   | 否   | 帧动画的插值模式。|
