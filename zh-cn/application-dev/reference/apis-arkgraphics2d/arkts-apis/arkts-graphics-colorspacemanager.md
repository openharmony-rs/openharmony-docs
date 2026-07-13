# @ohos.graphics.colorSpaceManager

本模块提供管理抽象化色域对象的一些基础能力，包括色域对象的创建与色域基础属性的获取等。

**起始版本：** 9

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [create](arkts-arkgraphics2d-create-f.md#create-1) | 创建标准色域对象。 |
| [create](arkts-arkgraphics2d-create-f.md#create-2) | 创建用户自定义色域对象。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ColorSpaceManager](arkts-arkgraphics2d-colorspacemanager-i.md) | 当前色域对象实例。下列API示例中都需先使用[create()](arkts-arkgraphics2d-create-f.md#create-1)获取到ColorSpaceManager实例，再通过此实例调用对应方法。 |
| [ColorSpacePrimaries](arkts-arkgraphics2d-colorspaceprimaries-i.md) | 色域标准三原色（红、绿、蓝）和白色，基于现实世界的色度，使用(x, y)表示其在色彩空间中的位置。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ColorSpace](arkts-arkgraphics2d-colorspace-e.md) | 色域类型枚举。 |

