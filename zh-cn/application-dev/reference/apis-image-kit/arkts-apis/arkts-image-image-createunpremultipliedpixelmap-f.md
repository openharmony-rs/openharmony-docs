# createUnpremultipliedPixelMap

## 导入模块

```TypeScript
import { image } from '@kit.ImageKit';
```

## createUnpremultipliedPixelMap

```TypeScript
function createUnpremultipliedPixelMap(src: PixelMap, dst: PixelMap, callback: AsyncCallback<void>): void
```

将PixelMap像素数据的透明度类型从预乘模式转换为非预乘模式，转换后的像素数据存入目标PixelMap。适用于需要对像素原始颜色值进行直接处理的场景，例如图像编辑、像素级分析等。使用callback异步回调。

> **说明：** 
> 
> - 该转换仅支持除RGBA_F16和ASTC_4x4之外其他包含Alpha通道的像素格式。
> - 由于图片占用内存较大，所以当PixelMap对象使用完成后，应主动调用[release](arkts-image-image-pixelmap-i.md#release)方法及时释放内存。 释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。

**起始版本：** 12

<!--Device-image-function createUnpremultipliedPixelMap(src: PixelMap, dst: PixelMap, callback: AsyncCallback<void>): void--><!--Device-image-function createUnpremultipliedPixelMap(src: PixelMap, dst: PixelMap, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | [PixelMap](arkts-image-image-pixelmap-i.md) | 是 | 源PixelMap对象，透明度类型需为预乘模式（AlphaType.PREMUL），像素格式必须包含Alpha通道（RGBA_F16和ASTC_4x4除外）。 |
| dst | [PixelMap](arkts-image-image-pixelmap-i.md) | 是 | 目标PixelMap对象，透明度类型需为非预乘模式（AlphaType.UNPREMUL）且必须可编辑，其他属性（宽度、高度、像素格式等）必须与源PixelMap相同，转换后的像素数据将写入该对象。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，当透明度类型转换成功时，err为undefined；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [62980103](../errorcode-image.md#62980103-图片类型不支持) | The image data is not supported. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [62980246](../errorcode-image.md#62980246-读取pixelmap失败) | Failed to read the pixelMap. |
| [62980248](../errorcode-image.md#62980248-pixelmap不允许修改) | Pixelmap not allow modify. |

**示例**

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

将PixelMap像素数据的透明度类型从预乘模式转换为非预乘模式，转换后的像素数据存入目标PixelMap。适用于需要对像素原始颜色值进行直接处理的场景，例如图像编辑、像素级分析等。使用Promise异步回调。

> **说明：** 
> 
> - 该转换仅支持除RGBA_F16和ASTC_4x4之外其他包含Alpha通道的像素格式。
> - 由于图片占用内存较大，所以当PixelMap对象使用完成后，应主动调用[release](arkts-image-image-pixelmap-i.md#release)方法及时释放内存。 释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。

**起始版本：** 12

<!--Device-image-function createUnpremultipliedPixelMap(src: PixelMap, dst: PixelMap): Promise<void>--><!--Device-image-function createUnpremultipliedPixelMap(src: PixelMap, dst: PixelMap): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | [PixelMap](arkts-image-image-pixelmap-i.md) | 是 | 源PixelMap对象，透明度类型需为预乘模式（AlphaType.PREMUL），像素格式必须包含Alpha通道（RGBA_F16和ASTC_4x4除外）。 |
| dst | [PixelMap](arkts-image-image-pixelmap-i.md) | 是 | 目标PixelMap对象，透明度类型需为非预乘模式（AlphaType.UNPREMUL）且必须可编辑，其他属性（宽度、高度、像素格式等）必须与源PixelMap相同，转换后的像素数据将写入该对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [62980103](../errorcode-image.md#62980103-图片类型不支持) | The image data is not supported. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [62980246](../errorcode-image.md#62980246-读取pixelmap失败) | Failed to read the pixelMap. |
| [62980248](../errorcode-image.md#62980248-pixelmap不允许修改) | Pixelmap not allow modify. |

**示例**

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
