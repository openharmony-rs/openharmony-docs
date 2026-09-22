# AtlasInterpolationMode（系统接口）

```TypeScript
enum AtlasInterpolationMode
```

定义精灵图序列帧动画的插值模式。

**起始版本：** 26.0.1

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## NONE

```TypeScript
NONE = 0
```

无插值。每一帧作为独立步骤单独显示。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## FRAME_BLEND

```TypeScript
FRAME_BLEND = 1
```

帧间插值。在相邻帧之间进行平滑过渡。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。
