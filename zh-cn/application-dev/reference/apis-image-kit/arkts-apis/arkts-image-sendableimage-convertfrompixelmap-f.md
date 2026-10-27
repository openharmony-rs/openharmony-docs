# convertFromPixelMap

## 导入模块

```TypeScript
import { sendableImage } from '@kit.ImageKit';
```

## convertFromPixelMap

```TypeScript
function convertFromPixelMap(pixelmap: image.PixelMap): PixelMap
```

通过image下的PixelMap创建出一个sendableImage下的PixelMap，同步返回PixelMap结果。原PixelMap的方法均不可再调用。

> **说明：** 
> 
> 由于图片占用内存较大，所以当PixelMap对象使用完成后，应主动调用[release](arkts-image-sendableimage-pixelmap-i.md#release)方法及时释放内存。 释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。

**起始版本：** 12

<!--Device-sendableImage-function convertFromPixelMap(pixelmap: image.PixelMap): PixelMap--><!--Device-sendableImage-function convertFromPixelMap(pixelmap: image.PixelMap): PixelMap-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pixelmap | [image.PixelMap](arkts-image-image-pixelmap-i.md) | 是 | image下的非Sendable的PixelMap。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PixelMap](arkts-image-sendableimage-pixelmap-i.md) | 成功同步返回Sendable的PixelMap对象，失败抛出异常。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | If the image parameter invalid. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [62980104](../errorcode-image.md#62980104-图片初始化错误) | Failed to initialize the internal object. |

**示例**

```TypeScript
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

function convertFromPixelMap() {
  const color: ArrayBuffer = new ArrayBuffer(96); // 96为需要创建的像素缓冲区大小，取值为：width * height * 4。
  const opts: image.InitializationOptions = { editable: true, pixelFormat: 3, size: { height: 4, width: 6 } };
  let pixelMap: image.PixelMap = image.createPixelMapSync(color, opts);
  try {
    let sendablePixelMap: sendableImage.PixelMap = sendableImage.convertFromPixelMap(pixelMap);
    console.info('Succeeded in converting the PixelMap.');
  } catch (error) {
    const err = error as BusinessError;
    console.error(`Failed to convert the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```
