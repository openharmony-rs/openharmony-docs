# Class (JfifMetadata)
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @XiaoYao555-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

JfifMetadata.

JFIF图像元数据类，用于存储图像的元数据。

> **说明：**
>
> 本模块同时支持ArkTS-Dyn、ArkTS-Sta。

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

## 导入模块

```ts
import { image } from '@kit.ImageKit';
```

## 属性

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

| 名称                         | 类型   | 只读 | 可选 | 说明                                       |
| ---------------------------- | ------ | ---- | ---- | ------------------------------------------ |
| densityUnit | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 是   | 用于定义Xdensity（水平像素密度）和Ydensity（垂直像素密度）的物理度量单位。<br>- 0表示无单位（仅像素宽高比）。<br>- 1表示每英寸像素数（DPI）。<br>- 2表示每厘米像素数（DPC）。<br>该值为正整数。 |
| xDensity | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 是   | JFIF图像X方向密度。<br>该值为正整数。 |
| yDensity | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 是   | JFIF图像Y方向密度。<br>该值为正整数。 |
| isProgressive | boolean | 是   | 是   | 图像是否采用渐进式编码，即图像在加载过程中按多次扫描逐步提升清晰度。true表示采用，false表示不采用。 |
| version | ArkTS-Dyn: number[] <br>ArkTS-Sta: int[] | 是   | 是   | JFIF图像版本。 |