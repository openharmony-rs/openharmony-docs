# GainmapChannel

```TypeScript
interface GainmapChannel
```

HDR增益图单个通道的数据内容，参考ISO 21496-1。

**起始版本：** 12

<!--Device-image-interface GainmapChannel--><!--Device-image-interface GainmapChannel-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## 导入模块

```TypeScript
import { image } from '@kit.ImageKit';
```

## alternateOffset

```TypeScript
alternateOffset: number
```

可选择图像的偏移量。浮点数，参考ISO 21496-1。

**类型：** number

**起始版本：** 12

<!--Device-GainmapChannel-alternateOffset: double--><!--Device-GainmapChannel-alternateOffset: double-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## baseOffset

```TypeScript
baseOffset: number
```

基础图的偏移量。浮点数，参考ISO 21496-1。

**类型：** number

**起始版本：** 12

<!--Device-GainmapChannel-baseOffset: double--><!--Device-GainmapChannel-baseOffset: double-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## gainmapMax

```TypeScript
gainmapMax: number
```

增益图的最大值。浮点数，取值范围是(0, +∞)且必须大于gainmapMin，参考ISO 21496-1。

**类型：** number

**起始版本：** 12

<!--Device-GainmapChannel-gainmapMax: double--><!--Device-GainmapChannel-gainmapMax: double-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## gainmapMin

```TypeScript
gainmapMin: number
```

增益图的最小值。浮点数，取值可以为0或负值但必须小于gainmapMax，参考ISO 21496-1。

**类型：** number

**起始版本：** 12

<!--Device-GainmapChannel-gainmapMin: double--><!--Device-GainmapChannel-gainmapMin: double-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## gamma

```TypeScript
gamma: number
```

增益曲线的Gamma校正值。浮点数，取值范围是(0, +∞)，参考ISO 21496-1。

**类型：** number

**起始版本：** 12

<!--Device-GainmapChannel-gamma: double--><!--Device-GainmapChannel-gamma: double-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core
