# @ohos.graphics.colorSpaceManager(色彩管理)

本模块提供管理抽象化色域对象的基础能力，包括创建标准色域对象（如SRGB、DCI-P3、BT2020等）和自定义色域对象，获取色域类型、白点值、gamma值等属性。适用于需要保证色彩一致性的场景，如图像处理、视频渲染、跨设备色彩显示等，帮助开发者实现准确的色彩管理和转换，提升应用在色彩显示方面的用户体验。

**起始版本：** 9

**系统能力：** SystemCapability.Graphic.Graphic2D.ColorManager.Core

## 导入模块

```TypeScript
import { colorSpaceManager } from '@kit.ArkGraphics2D';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [create](arkts-arkgraphics2d-colorspacemanager-create-f.md) | 创建标准色域对象。 |
| [create](arkts-arkgraphics2d-colorspacemanager-create-f.md) | 创建用户自定义色域对象。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ColorSpaceManager](arkts-arkgraphics2d-colorspacemanager-colorspacemanager-i.md) | 当前色域对象实例。 |
| [ColorSpacePrimaries](arkts-arkgraphics2d-colorspacemanager-colorspaceprimaries-i.md) | 色域标准三原色（红、绿、蓝）和白色，基于现实世界的色度，使用(x, y)表示其在色彩空间中的位置。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ColorSpace](arkts-arkgraphics2d-colorspacemanager-colorspace-e.md) | 色域类型枚举。 |
