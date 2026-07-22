# ImageReceiver

ImageReceiver类，用于获取组件surface id、接收最新的图片和读取下一张图片以及释放ImageReceiver实例。ImageReceiver作为图片的接收方和消费者，其参数属性实际上不会对接收到的图片产生影响。图片属性的配置应在发送方和生产者上进行，如相机预览流[createPreviewOutput](@ohos.multimedia.camera:camera.CameraManager.createPreviewOutput(profile: Profile, surfaceId: string))。

在调用以下方法前需要先通过[image.createImageReceiver](arkts-image-image-createimagereceiver-f.md#createimagereceiver)创建ImageReceiver实例。

从API version 23开始，更推荐使用[image.createImageReceiver](arkts-image-image-createimagereceiver-f.md#createimagereceiver)，通过传入[ImageReceiverOptions](arkts-image-image-imagereceiveroptions-i.md)创建ImageReceiver实例。

由于图片占用内存较大，所以当ImageReceiver实例使用完成后，应主动调用[release](arkts-image-image-imagereceiver-i.md#release)方法及时释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。
> **说明：**  
>  
> - 本Interface首批接口从API version 9开始支持。

**起始版本：** 9

<!--Device-image-interface ImageReceiver--><!--Device-image-interface ImageReceiver-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageReceiver

## 导入模块

```TypeScript
import { image } from '@kit.ImageKit';
```

## getReceivingSurfaceId

```TypeScript
getReceivingSurfaceId(callback: AsyncCallback<string>): void
```

用于获取一个surface id供Camera或其他组件使用。使用callback异步回调。

**起始版本：** 9

<!--Device-ImageReceiver-getReceivingSurfaceId(callback: AsyncCallback<string>): void--><!--Device-ImageReceiver-getReceivingSurfaceId(callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageReceiver

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | 是 | 回调函数，当获取surface id成功，err为undefined，data为获取到的surface id；否则为错误对象。 |

## getReceivingSurfaceId

```TypeScript
getReceivingSurfaceId(): Promise<string>
```

用于获取一个surface id供Camera或其他组件使用。使用Promise异步回调。

**起始版本：** 9

<!--Device-ImageReceiver-getReceivingSurfaceId(): Promise<string>--><!--Device-ImageReceiver-getReceivingSurfaceId(): Promise<string>-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageReceiver

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回surface id。 |

## off('imageArrival')

```TypeScript
off(type: 'imageArrival', callback?: AsyncCallback<void>): void
```

释放buffer时移除注册回调。使用callback异步回调。

**起始版本：** 13

<!--Device-ImageReceiver-off(type: 'imageArrival', callback?: AsyncCallback<void>): void--><!--Device-ImageReceiver-off(type: 'imageArrival', callback?: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageReceiver

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'imageArrival' | 是 | 注册事件的类型，固定为'imageArrival'，释放buffer时触发。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 否 | 移除的回调函数。 |

## on('imageArrival')

```TypeScript
on(type: 'imageArrival', callback: AsyncCallback<void>): void
```

接收图片时注册回调。使用callback异步回调。

**起始版本：** 9

<!--Device-ImageReceiver-on(type: 'imageArrival', callback: AsyncCallback<void>): void--><!--Device-ImageReceiver-on(type: 'imageArrival', callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageReceiver

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'imageArrival' | 是 | 注册事件的类型，固定为'imageArrival'，接收图片到达时触发。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，当注册事件触发成功，err为undefined，否则为错误对象。 |

## readLatestImage

```TypeScript
readLatestImage(callback: AsyncCallback<Image>): void
```

从ImageReceiver读取最新的图片。使用callback异步回调。
> **注意**：  
>  
> 此接口需要在[on](image.ImageReceiver.on(type: 'imageArrival', callback: AsyncCallback<void>))回调触发后调用，才能正常的接收到数  
> 据。且此接口返回的[Image](arkts-image-image-image-i.md)对象使用完毕后需要调用  
> [release](arkts-image-image-image-i.md#release)方法释放，释放后才可以继续接收新的数据。

**起始版本：** 9

<!--Device-ImageReceiver-readLatestImage(callback: AsyncCallback<Image>): void--><!--Device-ImageReceiver-readLatestImage(callback: AsyncCallback<Image>): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageReceiver

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Image&gt; | 是 | 回调函数，当读取最新图片成功，err为undefined，data为获取到的最新图片；否则为错误对象。 |

## readLatestImage

```TypeScript
readLatestImage(): Promise<Image>
```

从ImageReceiver读取最新的图片。使用Promise异步回调。
> **注意**：  
>  
> 此接口需要在[on](image.ImageReceiver.on(type: 'imageArrival', callback: AsyncCallback<void>))回调触发后调用，才能正常的接收到数  
> 据。且此接口返回的[Image](arkts-image-image-image-i.md)对象使用完毕后需要调用  
> [release](arkts-image-image-image-i.md#release)方法释放，释放后才可以继续接收新的数据。

**起始版本：** 9

<!--Device-ImageReceiver-readLatestImage(): Promise<Image>--><!--Device-ImageReceiver-readLatestImage(): Promise<Image>-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageReceiver

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Image&gt; | Promise对象，返回最新图片。 |

## readNextImage

```TypeScript
readNextImage(callback: AsyncCallback<Image>): void
```

从ImageReceiver读取下一张图片。使用callback异步回调。
> **注意**：  
>  
> 此接口需要在[on](image.ImageReceiver.on(type: 'imageArrival', callback: AsyncCallback<void>))回调触发后调用，才能正常的接收到数  
> 据。且此接口返回的[Image](arkts-image-image-image-i.md)对象使用完毕后需要调用  
> [release](arkts-image-image-image-i.md#release)方法释放，释放后才可以继续接收新的数据。

**起始版本：** 9

<!--Device-ImageReceiver-readNextImage(callback: AsyncCallback<Image>): void--><!--Device-ImageReceiver-readNextImage(callback: AsyncCallback<Image>): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageReceiver

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Image&gt; | 是 | 回调函数，当获取下一张图片成功，err为undefined，data为获取到的下一张图片；否则为错误对象。 |

## readNextImage

```TypeScript
readNextImage(): Promise<Image>
```

从ImageReceiver读取下一张图片。使用Promise异步回调。
> **注意**：  
>  
> 此接口需要在[on](image.ImageReceiver.on(type: 'imageArrival', callback: AsyncCallback<void>))回调触发后调用，才能正常的接收到数  
> 据。且此接口返回的[Image](arkts-image-image-image-i.md)对象使用完毕后需要调用  
> [release](arkts-image-image-image-i.md#release)方法释放，释放后才可以继续接收新的数据。

**起始版本：** 9

<!--Device-ImageReceiver-readNextImage(): Promise<Image>--><!--Device-ImageReceiver-readNextImage(): Promise<Image>-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageReceiver

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Image&gt; | Promise对象，返回下一张图片。 |

## release

```TypeScript
release(callback: AsyncCallback<void>): void
```

释放ImageReceiver实例。使用callback异步回调。

由于图片占用内存较大，所以当ImageReceiver实例使用完成后，应主动调用该方法，及时释放内存。

释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

**起始版本：** 9

<!--Device-ImageReceiver-release(callback: AsyncCallback<void>): void--><!--Device-ImageReceiver-release(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageReceiver

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，当释放ImageReceiver实例成功，err为undefined，否则为错误对象。 |

## release

```TypeScript
release(): Promise<void>
```

释放ImageReceiver实例。使用Promise异步回调。

由于图片占用内存较大，所以当ImageReceiver实例使用完成后，应主动调用该方法，及时释放内存。

释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

**起始版本：** 9

<!--Device-ImageReceiver-release(): Promise<void>--><!--Device-ImageReceiver-release(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageReceiver

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

## capacity

```TypeScript
readonly capacity: number
```

同时访问的图像数。该参数仅作为期望值，实际capacity由设备硬件决定。

**类型：** number

**起始版本：** 9

<!--Device-ImageReceiver-readonly capacity: int--><!--Device-ImageReceiver-readonly capacity: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageReceiver

## format

```TypeScript
readonly format: ImageFormat
```

图像格式，取值为[ImageFormat](arkts-image-image-imageformat-e.md)常量（目前仅支持 ImageFormat:JPEG，实际返回格式由生产者决定，如相机）。

**类型：** ImageFormat

**起始版本：** 9

<!--Device-ImageReceiver-readonly format: ImageFormat--><!--Device-ImageReceiver-readonly format: ImageFormat-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageReceiver

## size

```TypeScript
readonly size: Size
```

图片大小。该参数不会影响接收到的图片大小，实际返回大小由生产者决定，如相机。

**类型：** Size

**起始版本：** 9

<!--Device-ImageReceiver-readonly size: Size--><!--Device-ImageReceiver-readonly size: Size-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageReceiver

