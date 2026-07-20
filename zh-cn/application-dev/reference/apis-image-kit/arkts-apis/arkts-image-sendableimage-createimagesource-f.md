# createImageSource

## 导入模块

```TypeScript
import { sendableImage } from '@kit.ImageKit';
```

<a id="createimagesource"></a>
## createImageSource

```TypeScript
function createImageSource(uri: string): ImageSource
```

通过传入的uri创建ImageSource实例。

由于图片占用内存较大，所以当ImageSource实例使用完成后，应主动调用[release](arkts-image-sendableimage-pixelmap-i.md#release-1)方法及时释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-sendableImage-function createImageSource(uri: string): ImageSource--><!--Device-sendableImage-function createImageSource(uri: string): ImageSource-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 图片路径，当前仅支持应用沙箱路径。</br>当前支持格式有：.jpg .png .gif .bmp .webp .dng [SVG](docroot://reference/apis-image-kit/arkts-apis-image-f.md#svg标签说明) .ico。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ImageSource](arkts-image-sendableimage-imagesource-i.md) | 返回ImageSource类实例，失败时返回undefined。 |

**示例：**

```TypeScript
import { sendableImage } from '@kit.ImageKit';

async function CreateImageSource(context : Context) {
  const path: string = context.cacheDir + "/test.jpg";
  const sendableImageSourceObj: sendableImage.ImageSource = sendableImage.createImageSource(path);
}

```


<a id="createimagesource-1"></a>
## createImageSource

```TypeScript
function createImageSource(fd: number): ImageSource
```

通过传入文件描述符来创建ImageSource实例。

由于图片占用内存较大，所以当ImageSource实例使用完成后，应主动调用[release](arkts-image-sendableimage-pixelmap-i.md#release-1)方法及时释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-sendableImage-function createImageSource(fd: number): ImageSource--><!--Device-sendableImage-function createImageSource(fd: number): ImageSource-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 文件描述符fd。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ImageSource](arkts-image-sendableimage-imagesource-i.md) | 返回ImageSource类实例，失败时返回undefined。 |

**示例：**

```TypeScript
import { sendableImage } from '@kit.ImageKit';
import { fileIo } from '@kit.CoreFileKit';

async function CreateImageSource(context : Context) {
  const path: string = context.cacheDir + "/test.jpg";
  let file = fileIo.openSync(path, fileIo.OpenMode.CREATE | fileIo.OpenMode.READ_WRITE);
  const sendableImageSourceObj: sendableImage.ImageSource = sendableImage.createImageSource(file.fd);
}

```


<a id="createimagesource-2"></a>
## createImageSource

```TypeScript
function createImageSource(buf: ArrayBuffer): ImageSource
```

通过缓冲区创建ImageSource实例。buf数据是未解码的数据，不可以传入类似于RBGA，YUV的像素buffer数据，如果想通过像素buffer数据创建pixelMap，可以调用[sendableImage.createPixelMap](arkts-image-sendableimage-createpixelmap-f.md#createpixelmap-1)这一类方法。

由于图片占用内存较大，所以当ImageSource实例使用完成后，应主动调用[release](arkts-image-sendableimage-pixelmap-i.md#release-1)方法及时释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-sendableImage-function createImageSource(buf: ArrayBuffer): ImageSource--><!--Device-sendableImage-function createImageSource(buf: ArrayBuffer): ImageSource-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buf | ArrayBuffer | 是 | 图像缓冲区数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ImageSource](arkts-image-sendableimage-imagesource-i.md) | 返回ImageSource类实例，失败时返回undefined。 |

**示例：**

```TypeScript
import { sendableImage } from '@kit.ImageKit';

async function CreateImageSource() {
  const buf: ArrayBuffer = new ArrayBuffer(96); // 96为需要创建的像素buffer大小，取值为：height * width *4。
  const sendableImageSourceObj: sendableImage.ImageSource = sendableImage.createImageSource(buf);
}

```

