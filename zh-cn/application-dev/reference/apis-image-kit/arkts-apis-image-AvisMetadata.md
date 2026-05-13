# class (AvisMetadata)
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @baosiyuan-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

AvisMetadata.

AVIS图像元数据类，用于存储图像的元数据。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

## 导入模块

```ts
import { image } from '@kit.ImageKit';
```

## 属性

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

| 名称                         | 类型   | 只读 | 可选 | 说明                                       |
| ---------------------------- | ------ | ---- | ---- | ------------------------------------------ |
| delayTime | ArkTS-Dyn: number<br>ArkTS-Sta: int| 是   | 是   | AVIS图片的每帧播放时长。<br>该值为整数。单位为毫秒（ms）。 |