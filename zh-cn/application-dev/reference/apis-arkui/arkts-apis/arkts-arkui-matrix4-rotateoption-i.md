# RotateOption

旋转参数。

**起始版本：** 7

<!--Device-matrix4-interface RotateOption--><!--Device-matrix4-interface RotateOption-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { matrix4 } from '@kit.ArkUI';
```

## angle

```TypeScript
angle?: number
```

旋转角度。

默认值：0

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RotateOption-angle?: number--><!--Device-RotateOption-angle?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## centerX

```TypeScript
centerX?: number
```

单次矩阵变换中心点相对于组件变换中心点（锚点）的额外x轴偏移值。

单位：px

默认值：0

**说明：**

为0时表示x方向的矩阵变换中心恰好为组件x方向锚点，取值表示相对组件x方向锚点的额外偏移量。具体实现可参考[示例3（按中心点旋转）](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-transformation.md#示例3按中心点旋转)。

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RotateOption-centerX?: number--><!--Device-RotateOption-centerX?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## centerY

```TypeScript
centerY?: number
```

单次矩阵变换中心点相对于组件变换中心点（锚点）的额外y轴偏移值。

单位：px

默认值：0

**说明：**

为0时表示y方向的矩阵变换中心恰好为组件y方向锚点，取值表示相对组件y方向锚点的额外偏移量。具体实现可参考[示例3（按中心点旋转）](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-transformation.md#示例3按中心点旋转)。

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RotateOption-centerY?: number--><!--Device-RotateOption-centerY?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## x

```TypeScript
x?: number
```

旋转轴向量x坐标。

默认值：0。

取值范围 (-∞, +∞)

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RotateOption-x?: number--><!--Device-RotateOption-x?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## y

```TypeScript
y?: number
```

旋转轴向量y坐标。

默认值：0。

取值范围 (-∞, +∞)

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RotateOption-y?: number--><!--Device-RotateOption-y?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## z

```TypeScript
z?: number
```

旋转轴向量z坐标。

默认值：0。

取值范围 (-∞, +∞)。

**说明：** 旋转向量中x、y、z至少有一个不为0才有意义。

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RotateOption-z?: number--><!--Device-RotateOption-z?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

