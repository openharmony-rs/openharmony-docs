# PathMeasureMatrixFlags

路径测量中的矩阵信息维度枚举，常用于控制物体沿路径移动的动画场景。位置矩阵包含路径上某点的坐标平移信息； 切线矩阵包含路径上某点切线方向的旋转变换信息；位置和切线矩阵同时包含位置和切线信息，提供完整的路径几何信息。

**起始版本：** 23

<!--Device-drawing-enum PathMeasureMatrixFlags--><!--Device-drawing-enum PathMeasureMatrixFlags-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## GET_POSITION_MATRIX

```TypeScript
GET_POSITION_MATRIX = 0
```

获取位置信息对应的矩阵。

**起始版本：** 23

<!--Device-PathMeasureMatrixFlags-GET_POSITION_MATRIX = 0--><!--Device-PathMeasureMatrixFlags-GET_POSITION_MATRIX = 0-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## GET_TANGENT_MATRIX

```TypeScript
GET_TANGENT_MATRIX = 1
```

获取切线信息对应的矩阵。

**起始版本：** 23

<!--Device-PathMeasureMatrixFlags-GET_TANGENT_MATRIX = 1--><!--Device-PathMeasureMatrixFlags-GET_TANGENT_MATRIX = 1-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## GET_POSITION_AND_TANGENT_MATRIX

```TypeScript
GET_POSITION_AND_TANGENT_MATRIX = 2
```

获取位置和切线信息对应的矩阵。

**起始版本：** 23

<!--Device-PathMeasureMatrixFlags-GET_POSITION_AND_TANGENT_MATRIX = 2--><!--Device-PathMeasureMatrixFlags-GET_POSITION_AND_TANGENT_MATRIX = 2-End-->

**系统能力：** SystemCapability.Graphics.Drawing

