# MotionPathOptions

```TypeScript
declare interface MotionPathOptions
```

路径动画的运动路径参数选项。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## from

```TypeScript
from?: number
```

运动路径的起点位置比例。

默认值：0.0

取值范围：[0.0, 1.0]

设置小于0.0或大于1.0的值时，按默认值0.0处理。

from的处理值会约束to的取值，需满足to值 &gt;= from的处理值。当from等于to时（无论是开发者主动设置还是因超出范围被修正），组件在路径上不产生位移。

**类型：** number

**默认值：** 0.0

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## path

```TypeScript
path: string
```

位移动画的运动路径，使用[svg路径字符串](arkts-arkui-path-comp-pathoptions-i.md#commands)。path中支持使用start和end进行起点和终点的替代，如：'Mstart.x start.y L50 50 Lend.x end.y Z'，更多说明请参考[绘制路径](../../../ui/ui-js-components-svg-path.md)。

设置为空字符串时相当于不设置路径动画，传入不符合SVG路径规范的字符串时路径动画不生效。

**类型：** string

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## rotatable

```TypeScript
rotatable?: boolean
```

是否跟随路径进行旋转。true代表组件沿运动方向自动旋转（旋转角度由路径切线方向决定），false代表不跟随路径进行旋转。

默认值：false

**类型：** boolean

**默认值：** false

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## to

```TypeScript
to?: number
```

运动路径的终止位置比例。

取值原则：数值表示路径上的比例位置，0.0为路径起点，1.0为路径终点，中间值为路径上的对应比例位置。

默认值：1.0

取值范围：[0.0, 1.0]

设置小于0.0或大于1.0的值时，按默认值1.0处理，且满足to值 &gt;= 异常值处理后的from值。当处理后的to值小于异常值处理后的from值时，to值会被修正为等于异常值处理后的from值，即to被向上修正至与from相同。当from等于to时（无论是开发者主动设置还是因超出范围被修正），组件在路径上不产生位移。

**类型：** number

**默认值：** 1.0

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
