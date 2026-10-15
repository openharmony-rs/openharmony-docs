# HdrGainmapMetadata

```TypeScript
interface HdrGainmapMetadata
```

增益图使用的元数据值，[HdrMetadataKey](arkts-image-image-hdrmetadatakey-e.md)中HDR_GAINMAP_METADATA关键字对应的值，参考ISO 21496-1。

**起始版本：** 12

<!--Device-image-interface HdrGainmapMetadata--><!--Device-image-interface HdrGainmapMetadata-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## 导入模块

```TypeScript
import { image } from '@kit.ImageKit';
```

## alternateHeadroom

```TypeScript
alternateHeadroom: number
```

可选择图像的提亮比。取值范围是[1.0, +∞)，参考ISO 21496-1。

**类型：** number

**起始版本：** 12

<!--Device-HdrGainmapMetadata-alternateHeadroom: double--><!--Device-HdrGainmapMetadata-alternateHeadroom: double-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## baseHeadroom

```TypeScript
baseHeadroom: number
```

基础图的提亮比。取值范围是[1.0, +∞)，参考ISO 21496-1。

**类型：** number

**起始版本：** 12

<!--Device-HdrGainmapMetadata-baseHeadroom: double--><!--Device-HdrGainmapMetadata-baseHeadroom: double-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## channels

```TypeScript
channels: Array<GainmapChannel>
```

各通道的数据，长度为3，按R、G、B三通道存储，参考ISO 21496-1。

**类型：** Array&lt;[GainmapChannel](arkts-image-image-gainmapchannel-i.md)&gt;

**起始版本：** 12

<!--Device-HdrGainmapMetadata-channels: Array<GainmapChannel>--><!--Device-HdrGainmapMetadata-channels: Array<GainmapChannel>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## gainmapChannelCount

```TypeScript
gainmapChannelCount: number
```

增益图的颜色通道数。取值为1或3，值为3时RGB通道的元数据值不同，值为1时各通道元数据值相同，参考ISO 21496-1。

**类型：** number

**起始版本：** 12

<!--Device-HdrGainmapMetadata-gainmapChannelCount: int--><!--Device-HdrGainmapMetadata-gainmapChannelCount: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## miniVersion

```TypeScript
miniVersion: number
```

元数据解析所需的最小版本。

**类型：** number

**起始版本：** 12

<!--Device-HdrGainmapMetadata-miniVersion: int--><!--Device-HdrGainmapMetadata-miniVersion: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## useBaseColorFlag

```TypeScript
useBaseColorFlag: boolean
```

是否使用基础图的色彩空间。true表示使用，false表示不使用，参考ISO 21496-1。

**类型：** boolean

**起始版本：** 12

<!--Device-HdrGainmapMetadata-useBaseColorFlag: boolean--><!--Device-HdrGainmapMetadata-useBaseColorFlag: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## writerVersion

```TypeScript
writerVersion: number
```

元数据编写器的版本。

**类型：** number

**起始版本：** 12

<!--Device-HdrGainmapMetadata-writerVersion: int--><!--Device-HdrGainmapMetadata-writerVersion: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core
