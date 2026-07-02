# effectKit

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Multimedia-->
<!--Owner: @hanamaru-->
<!--Designer: @chensiyi_CE-->
<!--Tester: @zhaoxiaoguang2-->
<!--Adviser: @ge-yafang-->

## 概述

提供处理图像的基础能力，包括对当前图像的亮度调节、模糊化或灰度转换等。适用于需要在应用内快速实现图像滤镜效果的场景，如图像编辑、照片美化和相机滤镜等，帮助开发者无需关注底层算法实现即可快速完成图像效果处理功能，降低开发复杂度。

**系统能力：** SystemCapability.Multimedia.Image.Core

**起始版本：** 12
## 文件汇总

| 名称 | 描述 |
| -- | -- |
| [effect_filter.h](capi-effect-filter-h.md) | 声明滤镜效果的接口。该接口支持创建和管理多种滤镜效果，包括毛玻璃模糊、亮度调节、灰度转换、颜色反转等，支持通过自定义矩阵实现丰富的图像处理效果，适用于图像编辑、照片美化、视觉特效等场景。 |
| [effect_types.h](capi-effect-types-h.md) | 声明滤镜效果的数据类型，用于定义滤镜效果的矩阵、状态码和平铺模式等，支持创建自定义滤镜效果、处理图像着色器平铺等场景。 |
