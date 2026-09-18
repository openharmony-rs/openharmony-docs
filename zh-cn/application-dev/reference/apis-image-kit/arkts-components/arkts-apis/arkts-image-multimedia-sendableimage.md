# @ohos.multimedia.sendableImage

本模块基于[Sendable](../../../arkts-utils/arkts-sendable.md)对象，提供图片处理效果，包括通过属性创建PixelMap、读取图像像素数据、读取区域内的图片数据等。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## 导入模块

```TypeScript
import { sendableImage } from '@kit.ImageKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [convertFromPixelMap](arkts-image-sendableimage-convertfrompixelmap-f.md) | Creates a sendable image PixelMap from image PixelMap. |
| [convertToPixelMap](arkts-image-sendableimage-converttopixelmap-f.md) | Creates a image PixelMap from sendable image PixelMap. |
| [createImageReceiver](arkts-image-sendableimage-createimagereceiver-f.md) | 通过图片大小、图片格式、容量创建ImageReceiver实例。 |
| [createImageSource](arkts-image-sendableimage-createimagesource-f.md) | 通过传入的uri创建ImageSource实例。 |
| [createImageSource](arkts-image-sendableimage-createimagesource-f.md) | 通过传入文件描述符来创建ImageSource实例。 |
| [createImageSource](arkts-image-sendableimage-createimagesource-f.md) | 通过缓冲区创建ImageSource实例。buf数据是未解码的数据，不可以传入类似于RBGA，YUV的像素buffer数据，如果想通过像素buffer数据创建pixelMap，可以调用[sendableImage.createPixelMap](arkts-image-sendableimage-createpixelmap-f.md)这一类方法。 |
| [createPixelMap](arkts-image-sendableimage-createpixelmap-f.md) | Create PixelMap by data buffer. |
| [createPixelMapFromParcel](arkts-image-sendableimage-createpixelmapfromparcel-f.md) | Creates a PixelMap object based on MessageSequence parameter. |
| [createPixelMapFromSurface](arkts-image-sendableimage-createpixelmapfromsurface-f.md) | Creates a PixelMap object from surface id. |
| [createPixelMapSync](arkts-image-sendableimage-createpixelmapsync-f.md) | Create PixelMap by data buffer. |

### 接口

| 名称 | 说明 |
| --- | --- |
| [Image](arkts-image-sendableimage-image-i.md) | 提供基本的图像操作，包括获取图像信息、读写图像数据。调用[readNextImage](arkts-image-sendableimage-imagereceiver-i.md#readnextimage)和[readLatestImage](arkts-image-sendableimage-imagereceiver-i.md#readlatestimage)接口时会返回Image。继承自[ISendable](../../../arkts-utils/arkts-sendable.md#isendable)。 |
| [ImageReceiver](arkts-image-sendableimage-imagereceiver-i.md) | 图像接收类，用于获取组件Surface ID，接收最新的图片和读取下一张图片，以及释放ImageReceiver实例。 |
| [ImageSource](arkts-image-sendableimage-imagesource-i.md) | ImageSource类，用于获取图片相关信息。在调用ImageSource的方法前，需要先通过[sendableImage.createImageSource](arkts-image-sendableimage-createimagesource-f.md)构建一个ImageSource实例。 |
| [PixelMap](arkts-image-sendableimage-pixelmap-i.md) | Sendable PixelMap instance. |
| [Region](arkts-image-sendableimage-region-i.md) | 表示区域信息。 |
| [Size](arkts-image-sendableimage-size-i.md) | 表示图片尺寸。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ISendable](arkts-image-sendableimage-isendable-t.md) | ISendable是所有Sendable类型（除null和undefined）的父类型。自身没有任何必须的方法和属性。 |
