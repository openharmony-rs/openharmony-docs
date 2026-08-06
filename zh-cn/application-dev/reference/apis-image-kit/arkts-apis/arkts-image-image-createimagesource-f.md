# createImageSource

## createImageSource

```TypeScript
function createImageSource(uri: string): ImageSource
```

通过传入的uri创建ImageSource实例。 由于图片占用内存较大，所以当ImageSource实例使用完成后，应主动调用[release]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_方法及时 释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

**起始版本：** 6

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为6。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-image-function createImageSource(uri: string): ImageSource--><!--Device-image-function createImageSource(uri: string): ImageSource-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 图片路径，当前仅支持应用沙箱路径。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_当前支持格式有：JPEG、PNG、GIF、BMP、WebP、DNG、HEIC\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_3\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_12+\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_4\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_、WBMP\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_5\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_23+\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_6\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_、HEIFS\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_7\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_23+\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_8\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_、TIFF\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_9\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_23+\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_10\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_、SVG\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_11\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_10+\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_12\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_（可参考\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_）、ICO\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_13\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_11+\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_14\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。从API版本26.0.0开始，增加支持AVIF、AVIS格式。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_15\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_部分格式的解码能力依赖于具体的设备硬件，建议在调用前使用[image.getImageSourceSupportedFormats]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_接口，动态查询当前设备上的解码能力。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回ImageSource类实例，失败时返回undefined。 |

**示例：**

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

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-image-function createImageSource(uri: string): ImageSource | undefined--><!--Device-image-function createImageSource(uri: string): ImageSource | undefined-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | Image source URI. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | returns the ImageSource instance if the operation is successful; |


## createImageSource

```TypeScript
function createImageSource(uri: string, options: SourceOptions): ImageSource
```

通过传入的uri创建ImageSource实例。 由于图片占用内存较大，所以当ImageSource实例使用完成后，应主动调用[release]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_方法及时 释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-image-function createImageSource(uri: string, options: SourceOptions): ImageSource--><!--Device-image-function createImageSource(uri: string, options: SourceOptions): ImageSource-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 图片路径，当前仅支持应用沙箱路径（可参考\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_）。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_3\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_当前支持格式有：JPEG、PNG、GIF、BMP、WebP、DNG、HEIC\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_4\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_12+\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_5\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_、WBMP\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_6\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_23+\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_7\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_、HEIFS\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_8\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_23+\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_9\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_、TIFF\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_10\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_23+\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_11\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_、SVG\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_12\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_10+\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_13\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_（可参考\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_）、ICO\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_14\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_11+\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_15\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。从API版本26.0.0开始，增加支持AVIF、AVIS格式。部分格式的解码能力依赖于具体的设备硬件，建议在调用前使用[image.getImageSourceSupportedFormats]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_接口，动态查询当前设备上的解码能力。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 图片属性，包括图片像素密度、像素格式和图片尺寸。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回ImageSource类实例，失败时返回undefined。 |

**示例：**

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

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-image-function createImageSource(uri: string, options: SourceOptions): ImageSource | undefined--><!--Device-image-function createImageSource(uri: string, options: SourceOptions): ImageSource | undefined-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | Image source URI. |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | The config of Image source. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | Returns the ImageSource instance if the operation is successful; |


## createImageSource

```TypeScript
function createImageSource(fd: int): ImageSource
```

通过传入文件描述符来创建ImageSource实例。 由于图片占用内存较大，所以当ImageSource实例使用完成后，应主动调用[release]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_方法及时 释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

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
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回ImageSource类实例，失败时返回undefined。 |

**示例：**

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

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-image-function createImageSource(fd: int): ImageSource | undefined--><!--Device-image-function createImageSource(fd: int): ImageSource | undefined-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | int | 是 | ID of a file descriptor |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | Returns the ImageSource instance if the operation is successful; |


## createImageSource

```TypeScript
function createImageSource(fd: int, options: SourceOptions): ImageSource
```

通过传入文件描述符来创建ImageSource实例。 由于图片占用内存较大，所以当ImageSource实例使用完成后，应主动调用[release]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_方法及时 释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-image-function createImageSource(fd: int, options: SourceOptions): ImageSource--><!--Device-image-function createImageSource(fd: int, options: SourceOptions): ImageSource-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | int | 是 | 文件描述符fd。取值范围为[0，65535]。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 图片属性，包括图片像素密度、像素格式和图片尺寸。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回ImageSource类实例，失败时返回undefined。 |

**示例：**

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

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-image-function createImageSource(fd: int, options: SourceOptions): ImageSource | undefined--><!--Device-image-function createImageSource(fd: int, options: SourceOptions): ImageSource | undefined-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | int | 是 | ID of a file descriptor. |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | The config of Image source. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | Returns the ImageSource instance if the operation is successful; |


## createImageSource

```TypeScript
function createImageSource(buf: ArrayBuffer): ImageSource
```

通过缓冲区创建ImageSource实例。buf数据是未解码的数据，不可以传入类似于RBGA，YUV的像素buffer数据，如果想通过像素buffer数据创建pixelMap，可以调用 [image.createPixelMapSync]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_这一类接口。 由于图片占用内存较大，所以当ImageSource实例使用完成后，应主动调用[release]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_方法及时 释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

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
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回ImageSource类实例，失败时返回undefined。 |

**示例：**

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

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-image-function createImageSource(buf: ArrayBuffer): ImageSource | undefined--><!--Device-image-function createImageSource(buf: ArrayBuffer): ImageSource | undefined-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buf | ArrayBuffer | 是 | The buffer of the image. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | Returns the ImageSource instance if the operation is successful; |


## createImageSource

```TypeScript
function createImageSource(buf: ArrayBuffer, options: SourceOptions): ImageSource
```

通过缓冲区创建ImageSource实例。buf数据是未解码的数据，不可以传入类似于RBGA，YUV的像素buffer数据，如果想通过像素buffer数据创建pixelMap，可以调用 [image.createPixelMapSync]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_这一类接口。 由于图片占用内存较大，所以当ImageSource实例使用完成后，应主动调用[release]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_方法及时 释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-image-function createImageSource(buf: ArrayBuffer, options: SourceOptions): ImageSource--><!--Device-image-function createImageSource(buf: ArrayBuffer, options: SourceOptions): ImageSource-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buf | ArrayBuffer | 是 | 图像缓冲区数组。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 图片属性，包括图片像素密度、像素格式和图片尺寸。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回ImageSource类实例，失败时返回undefined。 |

**示例：**

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

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-image-function createImageSource(buf: ArrayBuffer, options: SourceOptions): ImageSource | undefined--><!--Device-image-function createImageSource(buf: ArrayBuffer, options: SourceOptions): ImageSource | undefined-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buf | ArrayBuffer | 是 | The buffer of the image. |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | The config of Image source. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | Returns the ImageSource instance if the operation is successful; |


## createImageSource

```TypeScript
function createImageSource(rawfile: resourceManager.RawFileDescriptor, options?: SourceOptions): ImageSource
```

通过图像资源文件的RawFileDescriptor创建ImageSource实例。 由于图片占用内存较大，所以当ImageSource实例使用完成后，应主动调用[release]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_方法及时 释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-image-function createImageSource(rawfile: resourceManager.RawFileDescriptor, options?: SourceOptions): ImageSource--><!--Device-image-function createImageSource(rawfile: resourceManager.RawFileDescriptor, options?: SourceOptions): ImageSource-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rawfile | resourceManager.RawFileDescriptor | 是 | 图像资源文件的RawFileDescriptor。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 图片属性，包括图片像素密度、像素格式和图片尺寸。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回ImageSource类实例，失败时返回undefined。 |

**示例：**

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

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-image-function createImageSource(rawfile: resourceManager.RawFileDescriptor, options?: SourceOptions)      : ImageSource | undefined--><!--Device-image-function createImageSource(rawfile: resourceManager.RawFileDescriptor, options?: SourceOptions)      : ImageSource | undefined-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rawfile | resourceManager.RawFileDescriptor | 是 | The raw file descriptor of the image. |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | The config of Image source. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | Returns the ImageSource instance if the operation is successful; |

