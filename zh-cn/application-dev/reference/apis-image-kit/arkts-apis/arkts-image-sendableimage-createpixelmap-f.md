# createPixelMap

## 导入模块

```TypeScript
import { sendableImage } from '@kit.ImageKit';
```

## createPixelMap

```TypeScript
function createPixelMap(colors: ArrayBuffer, options: image.InitializationOptions): Promise<PixelMap>
```

Create PixelMap by data buffer.

**起始版本：** 12

<!--Device-sendableImage-function createPixelMap(colors: ArrayBuffer, options: image.InitializationOptions): Promise<PixelMap>--><!--Device-sendableImage-function createPixelMap(colors: ArrayBuffer, options: image.InitializationOptions): Promise<PixelMap>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| colors | ArrayBuffer | 是 | The image color buffer. |
| options | image.InitializationOptions | 是 | Initialization options for PixelMap. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;PixelMap&gt; | A Promise instance used to return the PixelMap object. |

**示例**

```TypeScript
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

function createPixelMap() {
  const color: ArrayBuffer = new ArrayBuffer(96); // 96为需要创建的像素缓冲区大小，取值为：width * height * 4。
  let opts: image.InitializationOptions = {
    size: { height: 4, width: 6 },
    srcPixelFormat: image.PixelMapFormat.RGBA_8888, // 缓冲区中的源像素数据的像素格式。
    pixelFormat: image.PixelMapFormat.BGRA_8888, // 新创建的PixelMap的像素格式。
    editable: true
  };
  sendableImage.createPixelMap(color, opts).then((pixelMap: sendableImage.PixelMap) => {
    console.info('Succeeded in creating the PixelMap.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to create the PixelMap. Code: ${err.code}, message: ${err.message}`);
  });
}
```

