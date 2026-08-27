# convertFromPixelMap

## 导入模块

```TypeScript
import { sendableImage } from '@kit.ImageKit';
```

## convertFromPixelMap

```TypeScript
function convertFromPixelMap(pixelmap: image.PixelMap): PixelMap
```

Creates a sendable image PixelMap from image PixelMap.

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pixelmap | image.PixelMap | 是 | the src pixelmap. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PixelMap | Returns the instance if the operation is successful. Otherwise, an exception will be thrown. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | If the image parameter invalid. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
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
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to convert the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```
