# ImageCreator

ImageCreator类，作为图片的生产者，用于将图片写入到Surface中。

在调用以下方法前需要先通过[image.createImageCreator](arkts-image-image-createimagecreator-f.md#createimagecreator-1)创建ImageCreator实例，ImageCreator不支持多线程。

由于图片占用内存较大，所以当ImageCreator实例使用完成后，应主动调用[release](arkts-image-image-imagecreator-i.md#release-1)方法及时释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

> **说明：**  
>  
> - 本Interface首批接口从API version 9开始支持。

**起始版本：** 9

<!--Device-image-interface ImageCreator--><!--Device-image-interface ImageCreator-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageCreator

## 导入模块

```TypeScript
import { image } from '@kit.ImageKit';
```

## dequeueImage

```TypeScript
dequeueImage(callback: AsyncCallback<Image>): void
```

从空闲队列中获取buffer图片，用于绘制UI内容。使用callback异步回调。

**起始版本：** 9

<!--Device-ImageCreator-dequeueImage(callback: AsyncCallback<Image>): void--><!--Device-ImageCreator-dequeueImage(callback: AsyncCallback<Image>): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageCreator

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<Image> | 是 | 回调函数，当获取最新图片成功，err为undefined，data为获取到的最新图片；否则为错误对象。 |

## dequeueImage

```TypeScript
dequeueImage(): Promise<Image>
```

从空闲队列中获取buffer图片，用于绘制UI内容。使用Promise异步回调。

**起始版本：** 9

<!--Device-ImageCreator-dequeueImage(): Promise<Image>--><!--Device-ImageCreator-dequeueImage(): Promise<Image>-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageCreator

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Image> | Promise对象，返回最新图片。 |

## off('imageRelease')

```TypeScript
off(type: 'imageRelease', callback?: AsyncCallback<void>): void
```

释放buffer时，移除注册的回调函数。使用callback异步回调。

**起始版本：** 13

<!--Device-ImageCreator-off(type: 'imageRelease', callback?: AsyncCallback<void>): void--><!--Device-ImageCreator-off(type: 'imageRelease', callback?: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageCreator

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'imageRelease' | 是 | 监听事件类型，如'imageRelease'。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 否 | 回调函数。当移除注册成功时，err为undefined，否则为错误对象。 |

## on('imageRelease')

```TypeScript
on(type: 'imageRelease', callback: AsyncCallback<void>): void
```

监听imageRelease事件。使用callback异步回调。

**起始版本：** 9

<!--Device-ImageCreator-on(type: 'imageRelease', callback: AsyncCallback<void>): void--><!--Device-ImageCreator-on(type: 'imageRelease', callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageCreator

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'imageRelease' | 是 | 监听事件类型，如'imageRelease'。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数，当监听事件触发成功，err为undefined，否则为错误对象。 |

## queueImage

```TypeScript
queueImage(image: Image, callback: AsyncCallback<void>): void
```

将绘制好的图片放入队列。使用callback异步回调。

**起始版本：** 9

<!--Device-ImageCreator-queueImage(image: Image, callback: AsyncCallback<void>): void--><!--Device-ImageCreator-queueImage(image: Image, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageCreator

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| image | [Image](../../apis-arkgraphics3d/arkts-apis/arkts-arkgraphics3d-sceneresources-image-i.md) | 是 | 绘制好的buffer图像。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数，当将图片放入队列成功，err为undefined，否则为错误对象。 |

## queueImage

```TypeScript
queueImage(image: Image): Promise<void>
```

将绘制好的图片放入队列。使用Promise异步回调。

**起始版本：** 9

<!--Device-ImageCreator-queueImage(image: Image): Promise<void>--><!--Device-ImageCreator-queueImage(image: Image): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageCreator

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| image | [Image](../../apis-arkgraphics3d/arkts-apis/arkts-arkgraphics3d-sceneresources-image-i.md) | 是 | 绘制好的buffer图像。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

## release

```TypeScript
release(callback: AsyncCallback<void>): void
```

释放当前图像。使用callback异步回调。

由于图片占用内存较大，所以当ImageCreator实例使用完成后，应主动调用该方法，及时释放内存。

释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

**起始版本：** 9

<!--Device-ImageCreator-release(callback: AsyncCallback<void>): void--><!--Device-ImageCreator-release(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageCreator

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数，当图像释放成功，err为undefined，否则为错误对象。 |

## release

```TypeScript
release(): Promise<void>
```

释放当前图像。使用Promise异步回调。

由于图片占用内存较大，所以当ImageCreator实例使用完成后，应主动调用该方法，及时释放内存。

释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

**起始版本：** 9

<!--Device-ImageCreator-release(): Promise<void>--><!--Device-ImageCreator-release(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageCreator

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

## capacity

```TypeScript
readonly capacity: number
```

同时访问的图像数。该参数仅作为期望值，实际capacity由设备硬件决定。

**类型：** number

**起始版本：** 9

<!--Device-ImageCreator-readonly capacity: int--><!--Device-ImageCreator-readonly capacity: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageCreator

## format

```TypeScript
readonly format: ImageFormat
```

图像格式。

**类型：** ImageFormat

**起始版本：** 9

<!--Device-ImageCreator-readonly format: ImageFormat--><!--Device-ImageCreator-readonly format: ImageFormat-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageCreator

