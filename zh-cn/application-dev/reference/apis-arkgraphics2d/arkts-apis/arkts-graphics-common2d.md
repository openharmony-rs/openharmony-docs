# @ohos.graphics.common2D

本模块定义了一些2D图形领域的通用数据类型，包括颜色、矩形区域、坐标点等，适用于2D图形绘制等场景，为开发者提供了通用的图形数据结构，便于进行图形计算和渲染操作。

> **说明：**
> 
> - 本模块使用屏幕物理像素单位px。

**起始版本：** 11

**系统能力：** SystemCapability.Graphics.Drawing

## 导入模块

```TypeScript
import { common2D } from '@kit.ArkGraphics2D';
```

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [Color](arkts-arkgraphics2d-common2d-color-i.md) | ARGB格式的颜色描述。 |
| [Color4f](arkts-arkgraphics2d-common2d-color4f-i.md) | ARGB格式的颜色描述，颜色分量值为0.0~1.0的浮点数。 |
| [Point](arkts-arkgraphics2d-common2d-point-i.md) | 坐标点。 |
| [Point3d](arkts-arkgraphics2d-common2d-point3d-i.md) | 三维的坐标点。继承自[Point](arkts-arkgraphics2d-common2d-point-i.md)。 |
| [Rect](arkts-arkgraphics2d-common2d-rect-i.md) | 矩形区域，通过左上角点和右下角点两个坐标点定义。 |
