# @ohos.graphics.sendableColorSpaceManager

本模块提供管理抽象化色域对象的一些基础能力，包括可共享的色彩管理的创建与可共享的色域基础属性的获取等。

**起始版本：** 12

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [create](arkts-arkgraphics2d-create-f.md#create-1) | 创建标准可共享的色彩管理。 |
| [create](arkts-arkgraphics2d-create-f.md#create-2) | 创建用户自定义可共享的色彩管理实例。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ColorSpaceManager](arkts-arkgraphics2d-colorspacemanager-i.md) | 当前可共享的色彩管理实例。下列API示例中都需先使用[create()](arkts-arkgraphics2d-create-f.md#create-1)获取到ColorSpaceManager实例，再通过此实例调用对应方法。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ISendable](arkts-arkgraphics2d-isendable-t.md) | 为与当前模块的接口规范保持一致，重新定义了ISendable类型。 |

