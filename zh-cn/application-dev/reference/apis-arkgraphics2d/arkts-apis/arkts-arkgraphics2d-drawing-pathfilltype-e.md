# PathFillType

定义路径的填充类型枚举。
> **说明：**
> ![image_PathFillType_Winding_Even_Odd.png](../../../reference/apis-arkgraphics2d/figures/zh-ch_image_PathFillType_Winding_Even_Odd.png)
> 如图所示圆环为路径，箭头指示路径的方向，p为区域内任意一点，蓝色线条为点p出发的射线，黑色箭头所指为对应填充规则下使用蓝色填充路径的结果。WINDING填充规则下，射线与路径的交点计数为2，不为0，点p被涂色；EVEN_ODD  
> 填充规则下，射线与路径的相交次数为2，是偶数，点p不被涂色。

**起始版本：** 12

<!--Device-drawing-enum PathFillType--><!--Device-drawing-enum PathFillType-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## WINDING

```TypeScript
WINDING = 0
```

绘制区域中的任意一点，向任意方向射出一条射线，对于射线和路径的所有交点，初始计数为0，遇到每个顺时针的交点（路径从射线的左边向右穿过），计数加1，遇到每个逆时针的交点（路径从射线的右边向左穿过），计数减1，若最终的计数结果不为0，则认为这个点在路径内部，需要被涂色；若计数为0则不被涂色。

**起始版本：** 12

<!--Device-PathFillType-WINDING = 0--><!--Device-PathFillType-WINDING = 0-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## EVEN_ODD

```TypeScript
EVEN_ODD = 1
```

绘制区域中的任意一点，向任意方向射出一条射线，若这条射线和路径相交的次数是奇数，则这个点被认为在路径内部，需要被涂色；若是偶数则不被涂色。

**起始版本：** 12

<!--Device-PathFillType-EVEN_ODD = 1--><!--Device-PathFillType-EVEN_ODD = 1-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## INVERSE_WINDING

```TypeScript
INVERSE_WINDING = 2
```

WINDING涂色规则取反。

**起始版本：** 12

<!--Device-PathFillType-INVERSE_WINDING = 2--><!--Device-PathFillType-INVERSE_WINDING = 2-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## INVERSE_EVEN_ODD

```TypeScript
INVERSE_EVEN_ODD = 3
```

EVEN_ODD涂色规则取反。

**起始版本：** 12

<!--Device-PathFillType-INVERSE_EVEN_ODD = 3--><!--Device-PathFillType-INVERSE_EVEN_ODD = 3-End-->

**系统能力：** SystemCapability.Graphics.Drawing

