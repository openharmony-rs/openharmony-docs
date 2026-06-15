# Class (GifMetadata)
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @XiaoYao555-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

GifMetadata.

GIF图像元数据类，用于存储图像的元数据。

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
| delayTime | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 是   | GIF图片钳制后的帧延迟时长。钳制范围为[100, 65535]。<br>单位为毫秒（ms）。<br>该值为正整数。 |
| unclampedDelayTime | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 是   | GIF图片每帧未钳制的延迟时长。<br>单位为毫秒（ms）。<br>该值为正整数。 |
| hasGlobalColorMap | boolean | 是   | 是   | 是否包含全局调色板。<br>true表示包含，false表示不包含。 |
| loopCount |  ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 是   | GIF图片循环次数。<br>取值为0或正整数。0表示无限循环，其他值表示实际循环次数。 |
| disposalType |  ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 是   | GIF图片的每帧处置方式。<br>- 0表示未指定。<br>- 1表示不处置。<br>- 2表示还原为背景色。<br>- 3表示还原为前一帧。<br>该值为正整数。 |
| canvasHeight |  ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 是   | GIF图片的画布像素高度。<br>单位为像素（px）。 |
| canvasWidth | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 是   | GIF图片的画布像素宽度。<br>单位为像素（px）。 |