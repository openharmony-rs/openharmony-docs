# BlurType

定义蒙版滤镜模糊中操作类型的枚举。蒙版用于定义图像的可绘制区域，滤镜用于应用模糊等视觉效果。该枚举控制模糊效果如何应用到蒙版定义的区域内。 | 名称 | 值 | 说明 | 示意图 | | ------ | - | ------------------ | -------- | | NORMAL | 0 | 全面模糊，外圈和内部实体一起模糊。 |  | | SOLID | 1 | 内部实体不变，只模糊外圈边缘部分。 |  | | OUTER | 2 | 只有外圈边缘模糊，内部实体完全透明。 |  | | INNER | 3 | 只有内部实体模糊，外圈边缘清晰。 |  |

**起始版本：** 23

<!--Device-drawing-enum BlurType--><!--Device-drawing-enum BlurType-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## NORMAL

```TypeScript
NORMAL = 0
```

全面模糊，外圈边缘和内部实体一起模糊。

**起始版本：** 23

<!--Device-BlurType-NORMAL = 0--><!--Device-BlurType-NORMAL = 0-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## SOLID

```TypeScript
SOLID = 1
```

内部实体不变，只模糊外圈边缘部分。

**起始版本：** 23

<!--Device-BlurType-SOLID = 1--><!--Device-BlurType-SOLID = 1-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## OUTER

```TypeScript
OUTER = 2
```

只有外圈边缘模糊，内部实体完全透明。

**起始版本：** 23

<!--Device-BlurType-OUTER = 2--><!--Device-BlurType-OUTER = 2-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## INNER

```TypeScript
INNER = 3
```

只有内部实体模糊，外圈边缘清晰。

**起始版本：** 23

<!--Device-BlurType-INNER = 3--><!--Device-BlurType-INNER = 3-End-->

**系统能力：** SystemCapability.Graphics.Drawing

