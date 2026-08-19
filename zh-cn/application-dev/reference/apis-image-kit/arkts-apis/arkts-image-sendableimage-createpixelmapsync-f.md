# createPixelMapSync

## 导入模块

```TypeScript
import { sendableImage } from '@kit.ImageKit';
```

## createPixelMapSync

```TypeScript
function createPixelMapSync(colors: ArrayBuffer, options: image.InitializationOptions): PixelMap
```

Create PixelMap by data buffer.

**起始版本：** 12

<!--Device-sendableImage-function createPixelMapSync(colors: ArrayBuffer, options: image.InitializationOptions): PixelMap--><!--Device-sendableImage-function createPixelMapSync(colors: ArrayBuffer, options: image.InitializationOptions): PixelMap-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| colors | ArrayBuffer | 是 | The image color buffer. |
| options | image.InitializationOptions | 是 | Initialization options for PixelMap. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PixelMap | Returns the instance if the operation is successful;Otherwise, return undefined. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |

**示例**

```TypeScript
import { image } from '@kit.ImageKit';
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
    let pixelMap: sendableImage.PixelMap = sendableImage.createPixelMapSync(color, opts);
    if (pixelMap == undefined) {
      console.error(`Failed to create the PixelMap.`);
      return;
    }
    console.info('Succeeded in creating the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to create the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

