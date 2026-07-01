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
| [effect_filter.h](capi-effect-filter-h.md) | 声明滤镜效果的接口，包括创建、配置和销毁滤镜效果的相关方法，支持多种图像效果的叠加处理。 |
| [effect_types.h](capi-effect-types-h.md) | 声明滤镜效果的数据类型，定义了滤镜效果的枚举值和结构体，用于配置和传递滤镜效果参数。 |

## 错误码

| 错误码 | 描述 | 说明 |
| -- | -- | -- |
| EFFECT_BAD_PARAMETER = 401 | 无效的参数。 | 可能原因：参数类型不正确、参数值为空或参数值超出有效范围。解决措施：检查传入的参数类型是否符合接口要求，确保参数不为空且取值在接口规定的有效范围内。 |
| EFFECT_UNSUPPORTED_OPERATION = 7600201 | 不支持的操作。 | 可能原因：当前设备或系统版本不支持该操作。解决措施：确认操作的适用场景。 |
| EFFECT_UNKNOWN_ERROR = 7600901 | 未知错误。 | 可能原因：系统内部错误或资源异常。解决措施：检查系统资源状态（如内存、文件句柄等），确认资源是否充足；若为偶发性资源异常，可重启应用后重试。 |
