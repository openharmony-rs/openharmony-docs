# createImageSource

## 导入模块

```TypeScript
import { image } from '@kit.ImageKit';
```

## createImageSource

```TypeScript
function createImageSource(uri: string): ImageSource
```

通过传入的uri创建ImageSource实例。

由于图片占用内存较大，所以当ImageSource实例使用完成后，应主动调用[release](arkts-image-image-imagesource-i.md#release)方法及时释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

**起始版本：** 6

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-image-function createImageSource(uri: string): ImageSource--><!--Device-image-function createImageSource(uri: string): ImageSource-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 图片路径，当前仅支持应用沙箱路径。<br>当前支持格式有：JPEG、PNG、GIF、BMP、WebP、DNG、HEIC<sup>12+</sup>、WBMP<sup>23+</sup>、HEIFS<sup>23+</sup>、TIFF<sup>23+</sup>、SVG<sup>10+</sup>（可参考[SVG标签说明](../../../reference/apis-image-kit/arkts-apis-image-f.md#svg标签说明)）、ICO<sup>11+</sup>。从API版本26.0.0开始，增加支持AVIF、AVIS格式。<br>部分格式的解码能力依赖于具体的设备硬件，建议在调用前使用[image.getImageSourceSupportedFormats](arkts-image-image-getimagesourcesupportedformats-f.md#getimagesourcesupportedformats)接口，动态查询当前设备上的解码能力。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ImageSource](arkts-image-sendableimage-imagesource-i.md) | 返回ImageSource类实例，失败时返回undefined。 |

**示例：**

```TypeScript
async function CreateImageSource(context : Context) {
  // 此处'test.jpg'仅作示例，请开发者自行替换。否则imageSource会创建失败，导致后续无法正常执行。
  const path: string = context.filesDir + "/test.jpg";
  const imageSourceObj: image.ImageSource = image.createImageSource(path);
}

```


## createImageSource

```TypeScript
function createImageSource(uri: string, options: SourceOptions): ImageSource
```

通过传入的uri创建ImageSource实例。

由于图片占用内存较大，所以当ImageSource实例使用完成后，应主动调用[release](arkts-image-image-imagesource-i.md#release)方法及时释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-image-function createImageSource(uri: string, options: SourceOptions): ImageSource--><!--Device-image-function createImageSource(uri: string, options: SourceOptions): ImageSource-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 图片路径，当前仅支持应用沙箱路径（可参考[使用说明](../../../reference/apis-core-file-kit/js-apis-file-fs.md#使用说明)）。<br>当前支持格式有：JPEG、PNG、GIF、BMP、WebP、DNG、HEIC<sup>12+</sup>、WBMP<sup>23+</sup>、HEIFS<sup>23+</sup>、TIFF<sup>23+</sup>、SVG<sup>10+</sup>（可参考[SVG标签说明](../../../reference/apis-image-kit/arkts-apis-image-f.md#svg标签说明)）、ICO<sup>11+</sup>。从API版本26.0.0开始，增加支持AVIF、AVIS格式。部分格式的解码能力依赖于具体的设备硬件，建议在调用前使用[image.getImageSourceSupportedFormats](arkts-image-image-getimagesourcesupportedformats-f.md#getimagesourcesupportedformats)接口，动态查询当前设备上的解码能力。 |
| options | [SourceOptions](arkts-image-image-sourceoptions-i.md) | 是 | 图片属性，包括图片像素密度、像素格式和图片尺寸。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ImageSource](arkts-image-sendableimage-imagesource-i.md) | 返回ImageSource类实例，失败时返回undefined。 |

**示例：**

```TypeScript
async function CreateImageSource(context : Context) {
  let sourceOptions: image.SourceOptions = { sourceDensity: 120 };
  // 此处'test.png'仅作示例，请开发者自行替换。否则imageSource会创建失败，导致后续无法正常执行。
  const path: string = context.filesDir + "/test.png";
  let imageSourceObj: image.ImageSource = image.createImageSource(path, sourceOptions);
}

```


## createImageSource

```TypeScript
function createImageSource(fd: number): ImageSource
```

通过传入文件描述符来创建ImageSource实例。

由于图片占用内存较大，所以当ImageSource实例使用完成后，应主动调用[release](arkts-image-image-imagesource-i.md#release)方法及时释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-image-function createImageSource(fd: int): ImageSource--><!--Device-image-function createImageSource(fd: int): ImageSource-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 文件描述符fd。取值范围为[0，65535]。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ImageSource](arkts-image-sendableimage-imagesource-i.md) | 返回ImageSource类实例，失败时返回undefined。 |

**示例：**

```TypeScript
import { fileIo } from '@kit.CoreFileKit';

async function CreateImageSource(context : Context) {
  // 此处'test.jpg'仅作示例，请开发者自行替换，否则imageSource会创建失败导致后续无法正常执行。
  let filePath: string = context.filesDir + "/test.jpg";
  let file = fileIo.openSync(filePath, fileIo.OpenMode.CREATE | fileIo.OpenMode.READ_WRITE);
  const imageSourceObj: image.ImageSource = image.createImageSource(file.fd);
}

```


## createImageSource

```TypeScript
function createImageSource(fd: number, options: SourceOptions): ImageSource
```

通过传入文件描述符来创建ImageSource实例。

由于图片占用内存较大，所以当ImageSource实例使用完成后，应主动调用[release](arkts-image-image-imagesource-i.md#release)方法及时释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-image-function createImageSource(fd: int, options: SourceOptions): ImageSource--><!--Device-image-function createImageSource(fd: int, options: SourceOptions): ImageSource-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 文件描述符fd。取值范围为[0，65535]。 |
| options | [SourceOptions](arkts-image-image-sourceoptions-i.md) | 是 | 图片属性，包括图片像素密度、像素格式和图片尺寸。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ImageSource](arkts-image-sendableimage-imagesource-i.md) | 返回ImageSource类实例，失败时返回undefined。 |

**示例：**

```TypeScript
import { fileIo } from '@kit.CoreFileKit';

async function CreateImageSource(context : Context) {
  let sourceOptions: image.SourceOptions = { sourceDensity: 120 };
  // 此处'test.jpg'仅作示例，请开发者自行替换，否则imageSource创建失败会导致后续无法正常执行。
  const filePath: string = context.filesDir + "/test.jpg";
  let file = fileIo.openSync(filePath, fileIo.OpenMode.CREATE | fileIo.OpenMode.READ_WRITE);
  const imageSourceObj: image.ImageSource = image.createImageSource(file.fd, sourceOptions);
}

```


## createImageSource

```TypeScript
function createImageSource(buf: ArrayBuffer): ImageSource
```

通过缓冲区创建ImageSource实例。buf数据是未解码的数据，不可以传入类似于RBGA，YUV的像素buffer数据，如果想通过像素buffer数据创建pixelMap，可以调用[image.createPixelMapSync](arkts-image-image-createpixelmapsync-f.md#createpixelmapsync)这一类接口。

由于图片占用内存较大，所以当ImageSource实例使用完成后，应主动调用[release](arkts-image-image-imagesource-i.md#release)方法及时释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-image-function createImageSource(buf: ArrayBuffer): ImageSource--><!--Device-image-function createImageSource(buf: ArrayBuffer): ImageSource-End-->

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
async function CreateImageSource() {
  const buf: ArrayBuffer = new ArrayBuffer(96); // 96为需要创建的像素缓冲区大小，取值为：width * height * 4。
  const imageSourceObj: image.ImageSource = image.createImageSource(buf);
}

```


## createImageSource

```TypeScript
function createImageSource(buf: ArrayBuffer, options: SourceOptions): ImageSource
```

通过缓冲区创建ImageSource实例。buf数据是未解码的数据，不可以传入类似于RBGA，YUV的像素buffer数据，如果想通过像素buffer数据创建pixelMap，可以调用[image.createPixelMapSync](arkts-image-image-createpixelmapsync-f.md#createpixelmapsync)这一类接口。

由于图片占用内存较大，所以当ImageSource实例使用完成后，应主动调用[release](arkts-image-image-imagesource-i.md#release)方法及时释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-image-function createImageSource(buf: ArrayBuffer, options: SourceOptions): ImageSource--><!--Device-image-function createImageSource(buf: ArrayBuffer, options: SourceOptions): ImageSource-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buf | ArrayBuffer | 是 | 图像缓冲区数组。 |
| options | [SourceOptions](arkts-image-image-sourceoptions-i.md) | 是 | 图片属性，包括图片像素密度、像素格式和图片尺寸。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ImageSource](arkts-image-sendableimage-imagesource-i.md) | 返回ImageSource类实例，失败时返回undefined。 |

**示例：**

```TypeScript
async function CreateImageSource() {
  const data: ArrayBuffer = new ArrayBuffer(112);
  let sourceOptions: image.SourceOptions = { sourceDensity: 120 };
  const imageSourceObj: image.ImageSource = image.createImageSource(data, sourceOptions);
}

```


## createImageSource

```TypeScript
function createImageSource(rawfile: resourceManager.RawFileDescriptor, options?: SourceOptions): ImageSource
```

通过图像资源文件的RawFileDescriptor创建ImageSource实例。

由于图片占用内存较大，所以当ImageSource实例使用完成后，应主动调用[release](arkts-image-image-imagesource-i.md#release)方法及时释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-image-function createImageSource(rawfile: resourceManager.RawFileDescriptor, options?: SourceOptions): ImageSource--><!--Device-image-function createImageSource(rawfile: resourceManager.RawFileDescriptor, options?: SourceOptions): ImageSource-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rawfile | resourceManager.RawFileDescriptor | 是 | 图像资源文件的RawFileDescriptor。 |
| options | [SourceOptions](arkts-image-image-sourceoptions-i.md) | 否 | 图片属性，包括图片像素密度、像素格式和图片尺寸。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ImageSource](arkts-image-sendableimage-imagesource-i.md) | 返回ImageSource类实例，失败时返回undefined。 |

**示例：**

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';
  
async function CreateImageSource(context : Context) {
  // 获取resourceManager资源管理器。
  const resourceMgr: resourceManager.ResourceManager = context.resourceManager;
  // 此处'test.jpg'仅作示例，请开发者自行替换，否则imageSource创建失败会导致后续无法正常执行。
  resourceMgr.getRawFd('test.jpg').then((rawFileDescriptor: resourceManager.RawFileDescriptor) => {
    const imageSourceObj: image.ImageSource = image.createImageSource(rawFileDescriptor);
  }).catch((error: BusinessError) => {
    console.error(`Failed to get RawFileDescriptor.code is ${error.code}, message is ${error.message}`);
  })
}

```

