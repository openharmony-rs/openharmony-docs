# createImageSource

## createImageSource

```TypeScript
function createImageSource(uri: string): ImageSource
```

通过传入的uri创建ImageSource实例。 由于图片占用内存较大，所以当ImageSource实例使用完成后，应主动调用[release](arkts-image-image-imagesource-i.md#release)方法及时 释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

**起始版本：** 6

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为6。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-image-function createImageSource(uri: string): ImageSource--><!--Device-image-function createImageSource(uri: string): ImageSource-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 图片路径，当前仅支持应用沙箱路径。 &lt;br&gt;当前支持格式有：JPEG、PNG、GIF、BMP、WebP、DNG、HEIC&lt;sup&gt;12+&lt;/sup&gt;、WBMP&lt;sup&gt;23+&lt;/sup&gt;、HEIFS&lt;sup&gt;23+&lt;/sup&gt;、TIFF&lt;sup&gt;23+&lt;/ sup&gt;、SVG&lt;sup&gt;10+&lt;/sup&gt;（可参考[SVG标签说明](../../../reference/apis-image-kit/arkts-apis-image-f.md#svg标签说明)）、ICO&lt;sup&gt; 11+&lt;/sup&gt;。从API版本26.0.0开始，增加支持AVIF、AVIS格式。 &lt;br&gt;部分格式的解码能力依赖于具体的设备硬件，建议在调用前使用 [image.getImageSourceSupportedFormats](arkts-image-image-getimagesourcesupportedformats-f.md#getImageSourceSupportedFormats)接口，动态查询当前设备上的解码能力。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ImageSource | 返回ImageSource类实例，失败时返回undefined。 |

## 示例

ArkTS-Dyn示例：

```TypeScript
async function CreateImageSource(context : Context) {
  // 此处'test.jpg'仅作示例，请开发者自行替换。否则imageSource会创建失败，导致后续无法正常执行。
  const path: string = context.filesDir + "/test.jpg";
  const imageSourceObj: image.ImageSource = image.createImageSource(path);
}
```

ArkTS-Sta示例：

```TypeScript
import { common } from '@kit.AbilityKit';

function CreateImageSourceFunc(context: common.UIAbilityContext): image.ImageSource | undefined {
  let imageSource: image.ImageSource | undefined;
  try {
    // 此处'test_image.jpg'仅作示例，请开发者自行替换。否则imageSource会创建失败，导致后续无法正常执行。
    const sendBoxPath: string = context.filesDir + "/test_image.jpg";
    imageSource = image.createImageSource(sendBoxPath);
    if (imageSource != undefined) {
      console.info(0x00000, 'createImageSourceFunc', 'createImageSourceFunc success!');
    }
    return imageSource;
  } catch (err) {
    console.error(0x00000, 'createImageSourceFunc', 'createImageSourceFunc failed: ' + err);
    return undefined;
  }
}
```


## createImageSource

```TypeScript
function createImageSource(uri: string): ImageSource | undefined
```

Creates an ImageSource instance based on the URI.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-image-function createImageSource(uri: string): ImageSource | undefined--><!--Device-image-function createImageSource(uri: string): ImageSource | undefined-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | Image source URI. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ImageSource | returns the ImageSource instance if the operation is successful; returns undefined otherwise. |


## createImageSource

```TypeScript
function createImageSource(uri: string, options: SourceOptions): ImageSource
```

通过传入的uri创建ImageSource实例。 由于图片占用内存较大，所以当ImageSource实例使用完成后，应主动调用[release](arkts-image-image-imagesource-i.md#release)方法及时 释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-image-function createImageSource(uri: string, options: SourceOptions): ImageSource--><!--Device-image-function createImageSource(uri: string, options: SourceOptions): ImageSource-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 图片路径，当前仅支持应用沙箱路径（可参考使用说明） 。 &lt;br&gt;当前支持格式有：JPEG、PNG、GIF、BMP、WebP、DNG、HEIC&lt;sup&gt;12+&lt;/sup&gt;、WBMP&lt;sup&gt;23+&lt;/sup&gt;、HEIFS&lt;sup&gt;23+&lt;/sup&gt;、TIFF&lt;sup&gt;23+&lt;/ sup&gt;、SVG&lt;sup&gt;10+&lt;/sup&gt;（可参考[SVG标签说明](../../../reference/apis-image-kit/arkts-apis-image-f.md#svg标签说明)）、ICO&lt;sup&gt; 11+&lt;/sup&gt;。从API版本26.0.0开始，增加支持AVIF、AVIS格式。部分格式的解码能力依赖于具体的设备硬件，建议在调用前使用 [image.getImageSourceSupportedFormats](arkts-image-image-getimagesourcesupportedformats-f.md#getImageSourceSupportedFormats)接口，动态查询当前设备上的解码能力。 |
| options | [SourceOptions](arkts-image-image-sourceoptions-i.md) | 是 | 图片属性，包括图片像素密度、像素格式和图片尺寸。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ImageSource | 返回ImageSource类实例，失败时返回undefined。 |

## 示例

ArkTS-Dyn示例：

```TypeScript
async function CreateImageSource(context : Context) {
  let sourceOptions: image.SourceOptions = { sourceDensity: 120 };
  // 此处'test.png'仅作示例，请开发者自行替换。否则imageSource会创建失败，导致后续无法正常执行。
  const path: string = context.filesDir + "/test.png";
  let imageSourceObj: image.ImageSource = image.createImageSource(path, sourceOptions);
}
```

ArkTS-Sta示例：

```TypeScript
import { common } from '@kit.AbilityKit';

function CreateImageSourceFunc(context: common.UIAbilityContext): image.ImageSource | undefined {
  let imageSource: image.ImageSource | undefined;
  try {
    // 此处'test_image.jpg'仅作示例，请开发者自行替换。否则imageSource会创建失败，导致后续无法正常执行。
    const sendBoxPath: string = context.filesDir + "/test_image.jpg";
    let sourceOptions: image.SourceOptions = { sourceDensity: 120 };
    imageSource = image.createImageSource(sendBoxPath, sourceOptions);
    if (imageSource != undefined) {
      console.info(0x00000, 'createImageSourceFunc', 'createImageSourceFunc success!');
    }
    return imageSource;
  } catch (err) {
    console.error(0x00000, 'createImageSourceFunc', 'createImageSourceFunc failed: ' + err);
    return undefined;
  }
}
```


## createImageSource

```TypeScript
function createImageSource(uri: string, options: SourceOptions): ImageSource | undefined
```

Creates an ImageSource instance based on the URI.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-image-function createImageSource(uri: string, options: SourceOptions): ImageSource | undefined--><!--Device-image-function createImageSource(uri: string, options: SourceOptions): ImageSource | undefined-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | Image source URI. |
| options | [SourceOptions](arkts-image-image-sourceoptions-i.md) | 是 | The config of Image source. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ImageSource | Returns the ImageSource instance if the operation is successful; returns undefined otherwise. |


## createImageSource

```TypeScript
function createImageSource(fd: int): ImageSource
```

通过传入文件描述符来创建ImageSource实例。 由于图片占用内存较大，所以当ImageSource实例使用完成后，应主动调用[release](arkts-image-image-imagesource-i.md#release)方法及时 释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-image-function createImageSource(fd: int): ImageSource--><!--Device-image-function createImageSource(fd: int): ImageSource-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | int | 是 | 文件描述符fd。取值范围为[0，65535]。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ImageSource | 返回ImageSource类实例，失败时返回undefined。 |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { fileIo } from '@kit.CoreFileKit';

async function CreateImageSource(context : Context) {
  // 此处'test.jpg'仅作示例，请开发者自行替换，否则imageSource会创建失败导致后续无法正常执行。
  let filePath: string = context.filesDir + "/test.jpg";
  let file = fileIo.openSync(filePath, fileIo.OpenMode.CREATE | fileIo.OpenMode.READ_WRITE);
  const imageSourceObj: image.ImageSource = image.createImageSource(file.fd);
}
```

ArkTS-Sta示例：

```TypeScript
import { common } from '@kit.AbilityKit';
import { fileIo } from '@kit.CoreFileKit';

function CreateImageSourceFunc(context: common.UIAbilityContext): image.ImageSource | undefined {
  let imageSource: image.ImageSource;
  try {
    // 此处'test_image.jpg'仅作示例，请开发者自行替换，否则imageSource会创建失败导致后续无法正常执行。
    const filePath: string = context.filesDir + "/test_image.jpg";
    let file = fileIo.openSync(filePath, fileIo.OpenMode.CREATE | fileIo.OpenMode.READ_WRITE);
    imageSource = image.createImageSource(file.fd);
    if (imageSource != undefined) {
      console.info(0x00000, 'createImageSourceFunc', 'createImageSourceFunc success!');
    }
    return imageSource;
  } catch (err) {
    console.error(0x00000, 'createImageSourceFunc', 'createImageSourceFunc failed: ' + err);
    return undefined;
  }
}
```


## createImageSource

```TypeScript
function createImageSource(fd: int): ImageSource | undefined
```

Creates an ImageSource instance based on the file descriptor.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-image-function createImageSource(fd: int): ImageSource | undefined--><!--Device-image-function createImageSource(fd: int): ImageSource | undefined-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | int | 是 | ID of a file descriptor |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ImageSource | Returns the ImageSource instance if the operation is successful; returns undefined otherwise. |


## createImageSource

```TypeScript
function createImageSource(fd: int, options: SourceOptions): ImageSource
```

通过传入文件描述符来创建ImageSource实例。 由于图片占用内存较大，所以当ImageSource实例使用完成后，应主动调用[release](arkts-image-image-imagesource-i.md#release)方法及时 释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-image-function createImageSource(fd: int, options: SourceOptions): ImageSource--><!--Device-image-function createImageSource(fd: int, options: SourceOptions): ImageSource-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | int | 是 | 文件描述符fd。取值范围为[0，65535]。 |
| options | [SourceOptions](arkts-image-image-sourceoptions-i.md) | 是 | 图片属性，包括图片像素密度、像素格式和图片尺寸。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ImageSource | 返回ImageSource类实例，失败时返回undefined。 |

## 示例

ArkTS-Dyn示例：

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

ArkTS-Sta示例：

```TypeScript
import { common } from '@kit.AbilityKit';
import { fileIo } from '@kit.CoreFileKit';

function CreateImageSourceFunc(context: common.UIAbilityContext): image.ImageSource | undefined {
  let imageSource: image.ImageSource | undefined;
  try {
    // 此处'test_image.jpg'仅作示例，请开发者自行替换，否则imageSource会创建失败导致后续无法正常执行。
    const filePath: string = context.filesDir + "/test_image.jpg";
    let sourceOptions: image.SourceOptions = { sourceDensity: 120 };
    let file = fileIo.openSync(filePath, fileIo.OpenMode.CREATE | fileIo.OpenMode.READ_WRITE);
    imageSource = image.createImageSource(file.fd, sourceOptions);
    if (imageSource != undefined) {
      console.info(0x00000, 'createImageSourceFunc', 'createImageSourceFunc success!');
    }
    return imageSource;
  } catch (err) {
    console.error(0x00000, 'createImageSourceFunc', 'createImageSourceFunc failed: ' + err);
    return undefined;
  }
}
```


## createImageSource

```TypeScript
function createImageSource(fd: int, options: SourceOptions): ImageSource | undefined
```

Creates an ImageSource instance based on the file descriptor.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-image-function createImageSource(fd: int, options: SourceOptions): ImageSource | undefined--><!--Device-image-function createImageSource(fd: int, options: SourceOptions): ImageSource | undefined-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | int | 是 | ID of a file descriptor. |
| options | [SourceOptions](arkts-image-image-sourceoptions-i.md) | 是 | The config of Image source. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ImageSource | Returns the ImageSource instance if the operation is successful; returns undefined otherwise. |


## createImageSource

```TypeScript
function createImageSource(buf: ArrayBuffer): ImageSource
```

通过缓冲区创建ImageSource实例。buf数据是未解码的数据，不可以传入类似于RBGA，YUV的像素buffer数据，如果想通过像素buffer数据创建pixelMap，可以调用 [image.createPixelMapSync](arkts-image-image-createpixelmapsync-f.md#createPixelMapSync)这一类接口。 由于图片占用内存较大，所以当ImageSource实例使用完成后，应主动调用[release](arkts-image-image-imagesource-i.md#release)方法及时 释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

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
| ImageSource | 返回ImageSource类实例，失败时返回undefined。 |

## 示例

ArkTS-Dyn示例：

```TypeScript
async function CreateImageSource() {
  const buf: ArrayBuffer = new ArrayBuffer(96); // 96为需要创建的像素缓冲区大小，取值为：width * height * 4。
  const imageSourceObj: image.ImageSource = image.createImageSource(buf);
}
```

ArkTS-Sta示例：

```TypeScript
function CreateImageSourceFunc(): image.ImageSource | undefined {
  let imageSource: image.ImageSource | undefined;
  try {
    const buf: ArrayBuffer = new ArrayBuffer(96); // 96为需要创建的像素buffer大小，取值为：height * width * 4。
    imageSource = image.createImageSource(buf);
    if (imageSource != undefined) {
      console.info(0x00000, 'createImageSourceFunc', 'createImageSource success!');
    }
    return imageSource;
  } catch (err) {
    console.error(0x00000, 'createImageSourceFunc', 'createImageSourceFunc failed: ' + err);
    return undefined;
  }
}
```


## createImageSource

```TypeScript
function createImageSource(buf: ArrayBuffer): ImageSource | undefined
```

Creates an ImageSource instance based on the buffer.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-image-function createImageSource(buf: ArrayBuffer): ImageSource | undefined--><!--Device-image-function createImageSource(buf: ArrayBuffer): ImageSource | undefined-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buf | ArrayBuffer | 是 | The buffer of the image. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ImageSource | Returns the ImageSource instance if the operation is successful; returns undefined otherwise. |


## createImageSource

```TypeScript
function createImageSource(buf: ArrayBuffer, options: SourceOptions): ImageSource
```

通过缓冲区创建ImageSource实例。buf数据是未解码的数据，不可以传入类似于RBGA，YUV的像素buffer数据，如果想通过像素buffer数据创建pixelMap，可以调用 [image.createPixelMapSync](arkts-image-image-createpixelmapsync-f.md#createPixelMapSync)这一类接口。 由于图片占用内存较大，所以当ImageSource实例使用完成后，应主动调用[release](arkts-image-image-imagesource-i.md#release)方法及时 释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

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
| ImageSource | 返回ImageSource类实例，失败时返回undefined。 |

## 示例

ArkTS-Dyn示例：

```TypeScript
async function CreateImageSource() {
  const data: ArrayBuffer = new ArrayBuffer(112);
  let sourceOptions: image.SourceOptions = { sourceDensity: 120 };
  const imageSourceObj: image.ImageSource = image.createImageSource(data, sourceOptions);
}
```

ArkTS-Sta示例：

```TypeScript
function CreateImageSourceFunc(): image.ImageSource | undefined {
  let imageSource: image.ImageSource | undefined;
  try {
    const buf: ArrayBuffer = new ArrayBuffer(96); // 96为需要创建的像素buffer大小，取值为：height * width * 4。
    let sourceOptions: image.SourceOptions = { sourceDensity: 120 };
    imageSource = image.createImageSource(buf, sourceOptions);
    if (imageSource != undefined) {
      console.info(0x00000, 'createImageSourceFunc', 'createImageSource success!');
    }
    return imageSource;
  } catch (err) {
    console.error(0x00000, 'createImageSourceFunc', 'createImageSourceFunc failed: ' + err);
    return undefined;
  }
}
```


## createImageSource

```TypeScript
function createImageSource(buf: ArrayBuffer, options: SourceOptions): ImageSource | undefined
```

Creates an ImageSource instance based on the buffer.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-image-function createImageSource(buf: ArrayBuffer, options: SourceOptions): ImageSource | undefined--><!--Device-image-function createImageSource(buf: ArrayBuffer, options: SourceOptions): ImageSource | undefined-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buf | ArrayBuffer | 是 | The buffer of the image. |
| options | [SourceOptions](arkts-image-image-sourceoptions-i.md) | 是 | The config of Image source. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ImageSource | Returns the ImageSource instance if the operation is successful; returns undefined otherwise. |


## createImageSource

```TypeScript
function createImageSource(rawfile: resourceManager.RawFileDescriptor, options?: SourceOptions): ImageSource
```

通过图像资源文件的RawFileDescriptor创建ImageSource实例。 由于图片占用内存较大，所以当ImageSource实例使用完成后，应主动调用[release](arkts-image-image-imagesource-i.md#release)方法及时 释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

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
| ImageSource | 返回ImageSource类实例，失败时返回undefined。 |

## 示例

ArkTS-Dyn示例：

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

ArkTS-Sta示例：

```TypeScript
import { common } from '@kit.AbilityKit';
import { resourceManager } from '@kit.LocalizationKit';

function CreateImageSourceFunc(context: common.UIAbilityContext): image.ImageSource | undefined {
  let imageSource: image.ImageSource | undefined;
  try {
    const resourceMgr: resourceManager.ResourceManager = context.resourceManager;
    // 此处'test_image.jpg'仅作示例，请开发者自行替换，否则imageSource会创建失败导致后续无法正常执行。
    let rawFileDescriptor: resourceManager.RawFileDescriptor = await resourceMgr.getRawFd('test_image.jpg');

    imageSource = image.createImageSource(rawFileDescriptor);
    if (imageSource != undefined) {
      console.info(0x00000, 'createImageSourceFunc', 'createImageSource success!');
    }
    return imageSource;
  } catch (err) {
    console.error(0x00000, 'createImageSourceFunc', 'createImageSourceFunc failed: ' + err);
    return undefined;
  }
}
```


## createImageSource

```TypeScript
function createImageSource(rawfile: resourceManager.RawFileDescriptor, options?: SourceOptions)
      : ImageSource | undefined
```

Creates an ImageSource instance based on the raw file descriptor.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-image-function createImageSource(rawfile: resourceManager.RawFileDescriptor, options?: SourceOptions)      : ImageSource | undefined--><!--Device-image-function createImageSource(rawfile: resourceManager.RawFileDescriptor, options?: SourceOptions)      : ImageSource | undefined-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rawfile | resourceManager.RawFileDescriptor | 是 | The raw file descriptor of the image. |
| options | [SourceOptions](arkts-image-image-sourceoptions-i.md) | 否 | The config of Image source. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ImageSource | Returns the ImageSource instance if the operation is successful; returns undefined otherwise. |

