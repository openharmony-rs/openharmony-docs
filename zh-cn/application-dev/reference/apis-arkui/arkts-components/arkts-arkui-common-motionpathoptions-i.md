# MotionPathOptions

设置组件的运动路径。

**起始版本：** 7

<!--Device-unnamed-declare interface MotionPathOptions--><!--Device-unnamed-declare interface MotionPathOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## from

```TypeScript
from?: number
```

运动路径的起点。

默认值：0.0

取值范围：[0.0, 1.0]

设置小于0.0或大于1.0的值时，按默认值0.0处理。

**类型：** number

**默认值：** 0.0

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-MotionPathOptions-from?: number--><!--Device-MotionPathOptions-from?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## path

```TypeScript
path: string
```

位移动画的运动路径，使用[svg路径字符串](../../../../reference/apis-arkui/arkui-ts/ts-drawing-components-path.md#svg路径描述规范)。path中支持使用start和end进行起点和终点的替代，如：'Mstart.x start.y L50 50 Lend.x end.y Z'，更多说明请参考[绘制路径](../../../../ui/ui-js-components-svg-path.md)。

设置为空字符串时相当于不设置路径动画。

**类型：** string

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-MotionPathOptions-path: string--><!--Device-MotionPathOptions-path: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## rotatable

```TypeScript
rotatable?: boolean
```

是否跟随路径进行旋转。true代表跟随路径进行旋转，false代表不跟随路径进行旋转。

默认值：false

**类型：** boolean

**默认值：** false

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-MotionPathOptions-rotatable?: boolean--><!--Device-MotionPathOptions-rotatable?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## to

```TypeScript
to?: number
```

运动路径的终点。

默认值：1.0

取值范围：[0.0, 1.0]

设置小于0.0或大于1.0的值时，按默认值1.0处理，且满足to值 >= 异常值处理后的from值。

**类型：** number

**默认值：** 1.0

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-MotionPathOptions-to?: number--><!--Device-MotionPathOptions-to?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

