# class (WebPMetadata)
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @XiaoYao555-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

WebPMetadata

WebP图像元数据类，用于存储图像的元数据。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
> - 本模块首批接口从API version 24开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```ts
import { image } from '@kit.ImageKit';
```

## 属性

**ArkTS-Dyn起始版本：** 24

**ArkTS-Sta起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

| 名称                         | 类型   | 只读 | 可选 | 说明                                       |
| ---------------------------- | ------ | ---- | ---- | ------------------------------------------ |
| canvasWidth | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 是   | WebP图片的画布像素宽度。<br>单位为像素（px）。 |
| canvasHeight | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 是   | WebP图片的画布像素高度。<br>单位为像素（px）。 |
| delayTime | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 是   | WebP图片钳制后的帧延迟时长。钳制范围为[100, 65535]。<br>单位为毫秒（ms）。 |
| unclampedDelayTime | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 是   | WebP图片未钳制的帧延迟时长。<br>单位为毫秒（ms）。 |
| loopCount | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 是   | WebP图片动画循环的次数。如果取值为0，则表示不限次数。 |