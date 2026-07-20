# createPixelMapSync

## 导入模块

```TypeScript
import { image } from '@kit.ImageKit';
```

<a id="createpixelmapsync"></a>
## createPixelMapSync

```TypeScript
function createPixelMapSync(colors: ArrayBuffer, options: InitializationOptions): PixelMap
```

Create pixelmap by data buffer.

Starting from API 26.0.0, it is recommended to use {@link createPixelMapFromPixelsSync} instead for better exception handling capabilities.

**起始版本：** 12

<!--Device-image-function createPixelMapSync(colors: ArrayBuffer, options: InitializationOptions): PixelMap--><!--Device-image-function createPixelMapSync(colors: ArrayBuffer, options: InitializationOptions): PixelMap-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| colors | ArrayBuffer | 是 | The image color buffer. |
| options | [InitializationOptions](arkts-image-image-initializationoptions-i.md) | 是 | Initialization options for pixelmap. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PixelMap](arkts-image-image-pixelmap-i.md) | Returns the instance if the operation is successful;Otherwise, return undefined. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createPixelMapSync() {
  const color: ArrayBuffer = new ArrayBuffer(96); // 96为需要创建的像素缓冲区大小，取值为：width * height * 4。
  let opts: image.InitializationOptions = {
    size: { height: 4, width: 6 },
    srcPixelFormat: image.PixelMapFormat.RGBA_8888, // 缓冲区中的源像素数据的像素格式。
    pixelFormat: image.PixelMapFormat.BGRA_8888, // 新创建的PixelMap的像素格式。
    editable: true
  };
  try {
    let pixelMap: image.PixelMap = image.createPixelMapSync(color, opts);
    console.info('Succeeded in creating the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to create the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}

```


<a id="createpixelmapsync-1"></a>
## createPixelMapSync

```TypeScript
function createPixelMapSync(options: InitializationOptions): PixelMap
```

Create an empty pixelmap.

Starting from API 26.0.0, it is recommended to use {@link createEmptyPixelMap} instead for better exception handling capabilities.

**起始版本：** 12

<!--Device-image-function createPixelMapSync(options: InitializationOptions): PixelMap--><!--Device-image-function createPixelMapSync(options: InitializationOptions): PixelMap-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [InitializationOptions](arkts-image-image-initializationoptions-i.md) | 是 | Initialization options for pixelmap. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PixelMap](arkts-image-image-pixelmap-i.md) | Returns the instance if the operation is successful;Otherwise, return undefined. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createPixelMapSync() {
  let opts: image.InitializationOptions = { editable: true, pixelFormat: image.PixelMapFormat.RGBA_1010102, size: { height: 4, width: 6 } };
  try {
    let pixelMap: image.PixelMap = image.createPixelMapSync(opts);
    console.info('Succeeded in creating the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to create the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}

```

