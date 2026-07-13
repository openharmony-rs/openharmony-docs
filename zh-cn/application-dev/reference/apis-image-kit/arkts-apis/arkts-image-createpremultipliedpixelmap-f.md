# createPremultipliedPixelMap

## createPremultipliedPixelMap

```TypeScript
function createPremultipliedPixelMap(src: PixelMap, dst: PixelMap, callback: AsyncCallback<void>): void
```

Transforms pixelmap from unpremultiplied alpha format to premultiplied alpha format.

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | PixelMap | 是 | The source pixelmap. |
| dst | PixelMap | 是 | The destination pixelmap. |
| callback | AsyncCallback&lt;void&gt; | 是 | Callback used to return the operation result. |

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

function CreatePremultipliedPixelMap() {
  const color: ArrayBuffer = new ArrayBuffer(16); // 16为需要创建的像素缓冲区大小，取值为：width * height * 4。
  let bufferArr = new Uint8Array(color);
  for (let i = 0; i < bufferArr.length; i += 4) {
    bufferArr[i] = 255;
    bufferArr[i + 1] = 255;
    bufferArr[i + 2] = 122;
    bufferArr[i + 3] = 122;
  }
  let optsForUnpre: image.InitializationOptions = { editable: true, pixelFormat: image.PixelMapFormat.RGBA_8888, size: { height: 2, width: 2 } , alphaType: image.AlphaType.UNPREMUL}
  let srcPixelMap = image.createPixelMapSync(color, optsForUnpre);
  let optsForPre: image.InitializationOptions = { editable: true, pixelFormat: image.PixelMapFormat.RGBA_8888, size: { height: 2, width: 2 } , alphaType: image.AlphaType.PREMUL}
  let dstPixelMap = image.createPixelMapSync(optsForPre);
  image.createPremultipliedPixelMap(srcPixelMap, dstPixelMap, (error: BusinessError) => {
    if (error) {
      console.error(`Failed to convert PixelMap. Code is ${error.code}, message is ${error.message}`);
      return;
    }
    console.info('Succeeded in converting PixelMap.');
  });
}

```


## createPremultipliedPixelMap

```TypeScript
function createPremultipliedPixelMap(src: PixelMap, dst: PixelMap): Promise<void>
```

Transforms pixelmap from premultiplied alpha format to unpremultiplied alpha format.

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | PixelMap | 是 | The source pixelMap. |
| dst | PixelMap | 是 | The destination pixelmap. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | A Promise instance used to return the operation result.If the operation fails, an error message is returned. |

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

function CreatePremultipliedPixelMap() {
  const color: ArrayBuffer = new ArrayBuffer(16); // 16为需要创建的像素缓冲区大小，取值为：width * height * 4。
  let bufferArr = new Uint8Array(color);
  for (let i = 0; i < bufferArr.length; i += 4) {
    bufferArr[i] = 255;
    bufferArr[i + 1] = 255;
    bufferArr[i + 2] = 122;
    bufferArr[i + 3] = 122;
  }
  let optsForUnpre: image.InitializationOptions = { editable: true, pixelFormat: image.PixelMapFormat.RGBA_8888, size: { height: 2, width: 2 } , alphaType: image.AlphaType.UNPREMUL}
  let srcPixelMap = image.createPixelMapSync(color, optsForUnpre);
  let optsForPre: image.InitializationOptions = { editable: true, pixelFormat: image.PixelMapFormat.RGBA_8888, size: { height: 2, width: 2 } , alphaType: image.AlphaType.PREMUL}
  let dstPixelMap = image.createPixelMapSync(optsForPre);
  image.createPremultipliedPixelMap(srcPixelMap, dstPixelMap).then(() => {
    console.info('Succeeded in converting PixelMap.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to convert PixelMap. Code is ${error.code}, message is ${error.message}`);
  });
}

```

