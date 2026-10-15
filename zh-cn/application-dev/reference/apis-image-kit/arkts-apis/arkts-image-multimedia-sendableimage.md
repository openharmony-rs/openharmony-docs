# @ohos.multimedia.sendableImage

本模块基于[Sendable](../../../arkts-utils/arkts-sendable.md)对象，提供图片处理效果，包括通过属性创建PixelMap、读取图像像素数据、读取区域内的图片数据等。

**起始版本：** 12

<!--Device-unnamed-declare namespace sendableImage--><!--Device-unnamed-declare namespace sendableImage-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## 导入模块

```TypeScript
import { sendableImage } from '@kit.ImageKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [convertFromPixelMap](arkts-image-sendableimage-convertfrompixelmap-f.md#convertfrompixelmap) | 通过image下的PixelMap创建出一个sendableImage下的PixelMap，同步返回PixelMap结果。原PixelMap的方法均不可再调用。 |
| [convertToPixelMap](arkts-image-sendableimage-converttopixelmap-f.md#converttopixelmap) | 通过sendableImage下的PixelMap创建出一个image下的PixelMap，同步返回PixelMap结果。原PixelMap的方法均不可再调用。 |
| [createImageReceiver](arkts-image-sendableimage-createimagereceiver-f.md#createimagereceiver) | 通过图片大小、图片格式、容量创建ImageReceiver实例。 |
| [createImageSource](arkts-image-sendableimage-createimagesource-f.md#createimagesource1) | 通过传入的uri创建ImageSource实例。 |
| [createImageSource](arkts-image-sendableimage-createimagesource-f.md#createimagesource2) | 通过传入文件描述符来创建ImageSource实例。 |
| [createImageSource](arkts-image-sendableimage-createimagesource-f.md#createimagesource3) | 通过缓冲区创建ImageSource实例。buf数据是未解码的数据，不可以传入类似于RBGA，YUV的像素buffer数据，如果想通过像素buffer数据创建pixelMap，可以调用[sendableImage.createPixelMap](arkts-image-sendableimage-createpixelmap-f.md)这一类方法。 |
| [createPixelMap](arkts-image-sendableimage-createpixelmap-f.md#createpixelmap) | 通过像素数据和图像属性创建PixelMap。传入的像素数据会进行拷贝并转换为[InitializationOptions](arkts-image-image-initializationoptions-i.md).pixelFormat指定的像素格式，用于初始化PixelMap的像素。使用Promise异步回调。 |
| [createPixelMapFromParcel](arkts-image-sendableimage-createpixelmapfromparcel-f.md#createpixelmapfromparcel) | 从MessageSequence中反序列化并获取PixelMap。 |
| [createPixelMapFromSurface](arkts-image-sendableimage-createpixelmapfromsurface-f.md#createpixelmapfromsurface) | 根据Surface ID和区域信息创建一个PixelMap对象。该区域的大小由[Region](arkts-image-image-region-i.md).size指定。使用Promise异步回调。 |
| [createPixelMapSync](arkts-image-sendableimage-createpixelmapsync-f.md#createpixelmapsync) | 通过像素数据和图像属性创建PixelMap。传入的像素数据会进行拷贝并转换为[InitializationOptions](arkts-image-image-initializationoptions-i.md).pixelFormat指定的像素格式，用于初始化PixelMap的像素。同步返回结果。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [Image](arkts-image-sendableimage-image-i.md) | 提供基本的图像操作，包括获取图像信息、读写图像数据。调用[readNextImage](arkts-image-sendableimage-imagereceiver-i.md#readnextimage)和[readLatestImage](arkts-image-sendableimage-imagereceiver-i.md#readlatestimage)接口时会返回Image。继承自[ISendable](../../../arkts-utils/arkts-sendable.md#isendable)。 |
| [ImageReceiver](arkts-image-sendableimage-imagereceiver-i.md) | 图像接收类，用于获取组件Surface ID，接收最新的图片和读取下一张图片，以及释放ImageReceiver实例。 |
| [ImageSource](arkts-image-sendableimage-imagesource-i.md) | ImageSource类，用于获取图片相关信息。在调用ImageSource的方法前，需要先通过[sendableImage.createImageSource](arkts-image-sendableimage-createimagesource-f.md)构建一个ImageSource实例。 |
| [PixelMap](arkts-image-sendableimage-pixelmap-i.md) | 图像像素类，用于读取或写入图像数据以及获取图像信息，同时支持图像变换（缩放、平移、旋转、翻转、裁剪）、设置不透明度、提取Alpha通道、色彩空间设置等操作，适用于图像处理、图像编辑、图像显示等需要进行像素级数据操作的场景。在调用PixelMap的方法前，需要先通过[sendableImage.createPixelMap](arkts-image-sendableimage-createpixelmap-f.md)传入像素数据创建一个PixelMap对象。目前PixelMap序列化大小最大为128MiB，超过会渲染失败。PixelMap大小的计算方式为：宽 \* 高 \* 每像素占用字节数（详情请参考[PixelMapFormat](arkts-image-image-pixelmapformat-e.md)）。 |
| [Region](arkts-image-sendableimage-region-i.md) | 表示区域信息。 |
| [Size](arkts-image-sendableimage-size-i.md) | 表示图片尺寸。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ISendable](arkts-image-sendableimage-isendable-t.md) | ISendable是所有Sendable类型（除null和undefined）的父类型。自身没有任何必须的方法和属性。 |
