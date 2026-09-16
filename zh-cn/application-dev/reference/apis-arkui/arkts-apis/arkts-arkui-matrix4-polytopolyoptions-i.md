# PolyToPolyOptions

多边形到多边形的映射选项。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { matrix4 } from '@kit.ArkUI';
```

## dst

```TypeScript
dst:Array<Point>
```

目标多边形顶点坐标，用于定义映射变换的目标形状。

**类型：** Array&lt;[Point](arkts-arkui-matrix4-point-i.md)&gt;

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## dstIndex

```TypeScript
dstIndex?: number
```

目标点坐标起始索引，用于指定从dst数组中取目标点坐标的起始位置。

默认值: src.length/2

取值范围：[0, +∞)

**类型：** number

**默认值：** src.Length/2

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## pointCount

```TypeScript
pointCount?:number
```

使用到的点数量。前提条件：src和dst数组中的点数量需不少于pointCount。如果为0，则返回单位矩阵；如果为1，则使用1个源点和1个目标点，返回将源点平移到目标点的平移矩阵；如果为2，返回仿射变换矩阵（含旋转、缩放和平移）；如果为3，返回仿射变换矩阵（含旋转、缩放、平移和剪切）；如果为4，返回透视变换矩阵。超出范围时不生效。

默认值: 0

取值范围：[0, +∞)

**类型：** number

**默认值：** 0

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## src

```TypeScript
src: Array<Point>
```

源多边形顶点坐标，用于定义映射变换的起始形状。

**类型：** Array&lt;[Point](arkts-arkui-matrix4-point-i.md)&gt;

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## srcIndex

```TypeScript
srcIndex?: number
```

源点坐标起始索引，用于指定从src数组的哪个位置开始取点。当需要从src数组特定位置开始取源点时传入此参数，不传入时从索引0开始取点。

默认值：0

取值范围：[0, +∞)

**类型：** number

**默认值：** 0

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
