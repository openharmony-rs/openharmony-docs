# BlurType

定义蒙版滤镜模糊中操作类型的枚举。
| 名称 | 值 | 说明 | 示意图 |
| ------ | - | ------------------ | -------- |
| NORMAL | 0 | 全面模糊，外圈边缘和内部实体一起模糊。 | ![image_BlueType_Normal.png](../../../../reference/apis-arkgraphics2d/figures/zh-ch_image_BlueType_Normal.png) |
| SOLID | 1 | 内部实体不变，只模糊外圈边缘部分。 | ![image_BlueType_Solid.png](../../../../reference/apis-arkgraphics2d/figures/zh-ch_image_BlueType_Solid.png) |
| OUTER | 2 | 只有外圈边缘模糊，内部实体完全透明。 | ![image_BlueType_Outer.png](../../../../reference/apis-arkgraphics2d/figures/zh-ch_image_BlueType_Outer.png) |
| INNER | 3 | 只有内部实体模糊，外圈边缘清晰。 | ![image_BlueType_Inner.png](../../../../reference/apis-arkgraphics2d/figures/zh-ch_image_BlueType_Inner.png) |

**起始版本：** 12

**系统能力：** SystemCapability.Graphics.Drawing

## NORMAL

```TypeScript
NORMAL = 0
```

Both the outer edges and the inner solid parts are blurred.

**起始版本：** 12

**系统能力：** SystemCapability.Graphics.Drawing

## SOLID

```TypeScript
SOLID = 1
```

The inner solid part remains unchanged, while only the outer edges are blurred.

**起始版本：** 12

**系统能力：** SystemCapability.Graphics.Drawing

## OUTER

```TypeScript
OUTER = 2
```

Only the outer edges are blurred, with the inner solid part being fully transparent.

**起始版本：** 12

**系统能力：** SystemCapability.Graphics.Drawing

## INNER

```TypeScript
INNER = 3
```

Only the inner solid part is blurred, while the outer edges remain sharp.

**起始版本：** 12

**系统能力：** SystemCapability.Graphics.Drawing

