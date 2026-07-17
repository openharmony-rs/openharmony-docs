# createUnpremultipliedPixelMap

## 导入模块

```TypeScript
import { image } from '@kit.ImageKit';
```

## createUnpremultipliedPixelMap

```TypeScript
function createUnpremultipliedPixelMap(src: PixelMap, dst: PixelMap, callback: AsyncCallback<void>): void
```

Transforms pixelmap from premultiplied alpha format to unpremultiplied alpha format.

**起始版本：** 12

<!--Device-image-function createUnpremultipliedPixelMap(src: PixelMap, dst: PixelMap, callback: AsyncCallback<void>): void--><!--Device-image-function createUnpremultipliedPixelMap(src: PixelMap, dst: PixelMap, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | [PixelMap](arkts-image-image-pixelmap-i.md) | 是 | The source pixelmap. |
| dst | [PixelMap](arkts-image-image-pixelmap-i.md) | 是 | The destination pixelmap. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | Callback used to return the operation result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [62980103](../errorcode-image.md#62980103-图片类型不支持) | The image data is not supported. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. |
| [62980246](../errorcode-image.md#62980246-读取pixelmap失败) | Failed to read the pixelMap. |
| [62980248](../errorcode-image.md#62980248-pixelmap不允许修改) | Pixelmap not allow modify. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createUnpremultipliedPixelMap() {
  const color: ArrayBuffer = new ArrayBuffer(16); // 16为需要创建的像素缓冲区大小，取值为：width * height * 4。
  let bufferArr = new Uint8Array(color);
  for (let i = 0; i < bufferArr.length; i += 4) {
    bufferArr[i] = 255;
    bufferArr[i + 1] = 255;
    bufferArr[i + 2] = 122;
    bufferArr[i + 3] = 122;
  }
  let optsForPre: image.InitializationOptions = { editable: true, pixelFormat: image.PixelMapFormat.RGBA_8888, size: { height: 2, width: 2 }, alphaType: image.AlphaType.PREMUL};
  let srcPixelMap = image.createPixelMapSync(color, optsForPre);
  let optsForUnpre: image.InitializationOptions = { editable: true, pixelFormat: image.PixelMapFormat.RGBA_8888, size: { height: 2, width: 2 }, alphaType: image.AlphaType.UNPREMUL};
  let dstPixelMap = image.createPixelMapSync(optsForUnpre);
  image.createUnpremultipliedPixelMap(srcPixelMap, dstPixelMap, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to convert the PixelMap. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in converting the PixelMap.');
  });
}

```


## createUnpremultipliedPixelMap

```TypeScript
function createUnpremultipliedPixelMap(src: PixelMap, dst: PixelMap): Promise<void>
```

Transforms pixelmap from premultiplied alpha format to unpremultiplied alpha format.

**起始版本：** 12

<!--Device-image-function createUnpremultipliedPixelMap(src: PixelMap, dst: PixelMap): Promise<void>--><!--Device-image-function createUnpremultipliedPixelMap(src: PixelMap, dst: PixelMap): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | [PixelMap](arkts-image-image-pixelmap-i.md) | 是 | The source pixelmap. |
| dst | [PixelMap](arkts-image-image-pixelmap-i.md) | 是 | The destination pixelmap. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | A Promise instance used to return the operation result.If the operation fails, an error message is returned. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [62980103](../errorcode-image.md#62980103-图片类型不支持) | The image data is not supported. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. |
| [62980246](../errorcode-image.md#62980246-读取pixelmap失败) | Failed to read the pixelMap. |
| [62980248](../errorcode-image.md#62980248-pixelmap不允许修改) | Pixelmap not allow modify. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createUnpremultipliedPixelMap() {
  const color: ArrayBuffer = new ArrayBuffer(16); // 16为需要创建的像素缓冲区大小，取值为：width * height * 4。
  let bufferArr = new Uint8Array(color);
  for (let i = 0; i < bufferArr.length; i += 4) {
    bufferArr[i] = 255;
    bufferArr[i + 1] = 255;
    bufferArr[i + 2] = 122;
    bufferArr[i + 3] = 122;
  }
  let optsForPre: image.InitializationOptions = { editable: true, pixelFormat: image.PixelMapFormat.RGBA_8888, size: { height: 2, width: 2 }, alphaType: image.AlphaType.PREMUL};
  let srcPixelMap = image.createPixelMapSync(color, optsForPre);
  let optsForUnpre: image.InitializationOptions = { editable: true, pixelFormat: image.PixelMapFormat.RGBA_8888, size: { height: 2, width: 2 }, alphaType: image.AlphaType.UNPREMUL};
  let dstPixelMap = image.createPixelMapSync(optsForUnpre);
  image.createUnpremultipliedPixelMap(srcPixelMap, dstPixelMap).then(() => {
    console.info('Succeeded in converting the PixelMap.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to convert the PixelMap. Code: ${err.code}, message: ${err.message}`);
  });
}

```

