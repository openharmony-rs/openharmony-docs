# RotateOption

旋转参数。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { matrix4 } from '@kit.ArkUI';
```

## angle

```TypeScript
angle?: number
```

旋转角度，用于设置组件绕旋转轴的旋转量。当需要旋转组件时传入此参数，不传入时组件不做旋转。

单位为度（°）

默认值：0

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## centerX

```TypeScript
centerX?: number
```

单次矩阵变换操作的中心点相对于组件变换中心点（锚点）的额外x轴偏移值。

单位：px

默认值：0

**说明：** 

为0时表示x方向的矩阵变换中心恰好为组件x方向锚点，取值表示相对组件x方向锚点的额外偏移量。具体实现可参考[示例3（按中心点旋转）](arkts-arkui-matrix4.md)。

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## centerY

```TypeScript
centerY?: number
```

单次矩阵变换中心点相对于组件变换中心点（锚点）的额外y轴偏移值。

单位：px

默认值：0

**说明：** 

为0时表示y方向的矩阵变换中心恰好为组件y方向锚点，取值表示相对组件y方向锚点的额外偏移量。具体实现可参考[示例3（按中心点旋转）](arkts-arkui-matrix4.md)。

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## x

```TypeScript
x?: number
```

旋转轴向量x坐标，用于指定旋转轴在x方向的分量。当需要绕包含x分量的轴旋转时传入此参数，不传入时旋转轴x分量默认为0。

**说明：** 旋转向量中x、y、z至少有一个不为0才有意义。

默认值：0

取值范围：(-∞, +∞)

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## y

```TypeScript
y?: number
```

旋转轴向量y坐标，用于指定旋转轴在y方向的分量。当需要绕包含y分量的轴旋转时传入此参数，不传入时旋转轴y分量默认为0。

**说明：** 旋转向量中x、y、z至少有一个不为0才有意义。

默认值：0

取值范围：(-∞, +∞)

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## z

```TypeScript
z?: number
```

旋转轴向量z坐标，用于指定旋转轴在z方向的分量。当需要绕包含z分量的轴旋转时传入此参数，不传入时旋转轴z分量默认为0。

默认值：0

取值范围 (-∞, +∞)。

**说明：** 旋转向量中x、y、z至少有一个不为0，否则不产生旋转效果。

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
