# ImageSource

ImageSource类，用于获取图片相关信息。在调用ImageSource的方法前，需要先通过[sendableImage.createImageSource](arkts-image-sendableimage-createimagesource-f.md#createimagesource)构建一个ImageSource实例。

由于图片占用内存较大，所以当ImageSource实例使用完成后，应主动调用[release](arkts-image-sendableimage-pixelmap-i.md#release)方法及时释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

**起始版本：** 12

<!--Device-sendableImage-interface ImageSource--><!--Device-sendableImage-interface ImageSource-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

## 导入模块

```TypeScript
import { sendableImage } from '@kit.ImageKit';
```

## createPixelMap

```TypeScript
createPixelMap(options?: image.DecodingOptions): Promise<PixelMap>
```

通过图片解码参数创建PixelMap对象。使用Promise异步回调。

由于图片占用内存较大，所以当PixelMap对象使用完成后，应主动调用[release](arkts-image-sendableimage-pixelmap-i.md#release)方法及时释放内存。释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageSource-createPixelMap(options?: image.DecodingOptions): Promise<PixelMap>--><!--Device-ImageSource-createPixelMap(options?: image.DecodingOptions): Promise<PixelMap>-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | image.DecodingOptions | 否 | 解码参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;PixelMap&gt; | Promise实例，用于异步返回创建结果。 |

**示例：**

```TypeScript
import { sendableImage } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function CreatePixelMap(context : Context) {
  const path: string = context.cacheDir + "/test.jpg";
  const sendableImageSourceObj: sendableImage.ImageSource = sendableImage.createImageSource(path);
  sendableImageSourceObj.createPixelMap().then((pixelMap: sendableImage.PixelMap) => {
    console.info('Succeeded in creating pixelMap object through image decoding parameters.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to create pixelMap object through image decoding parameters. code ${error.code}, message is ${error.message}`);
  })
}

```

## release

```TypeScript
release(): Promise<void>
```

释放ImageSource实例。使用Promise异步回调。

由于图片占用内存较大，所以当ImageSource实例使用完成后，应主动调用该方法，及时释放内存。

释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

**起始版本：** 12

<!--Device-ImageSource-release(): Promise<void>--><!--Device-ImageSource-release(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise实例，异步返回结果。 |

**示例：**

```TypeScript
import { sendableImage } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function Release(context : Context) {
  const path: string = context.cacheDir + "/test.jpg";
  const sendableImageSourceObj: sendableImage.ImageSource = sendableImage.createImageSource(path);
  sendableImageSourceObj.release().then(() => {
    console.info('Succeeded in releasing the image source instance.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to release the image source instance. code ${error.code}, message is ${error.message}`);
  })
}

```

