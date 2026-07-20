# createPixelMapFromSurface

## 导入模块

```TypeScript
import { sendableImage } from '@kit.ImageKit';
```

<a id="createpixelmapfromsurface"></a>
## createPixelMapFromSurface

```TypeScript
function createPixelMapFromSurface(surfaceId: string, region: image.Region): Promise<PixelMap>
```

Creates a PixelMap object from surface id.

**起始版本：** 12

<!--Device-sendableImage-function createPixelMapFromSurface(surfaceId: string, region: image.Region): Promise<PixelMap>--><!--Device-sendableImage-function createPixelMapFromSurface(surfaceId: string, region: image.Region): Promise<PixelMap>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| surfaceId | string | 是 | surface id. |
| region | image.Region | 是 | The region to surface. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;PixelMap&gt; | Returns the instance if the operation is successful.Otherwise, an exception will be thrown. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [62980115](../errorcode-image.md#62980115-图片无效参数) | If the image parameter invalid. |
| [62980105](../errorcode-image.md#62980105-图片获取数据错误) | Failed to get the data. |
| [62980178](../errorcode-image.md#62980178-pixelmap创建失败) | Failed to create the PixelMap. |

**示例：**

```TypeScript

import { sendableImage } from '@kit.ImageKit';
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function CreatePixelMapFromSurface(surfaceId: string) {
  let region: image.Region = { x: 0, y: 0, size: { height: 100, width: 100 } };
  sendableImage.createPixelMapFromSurface(surfaceId, region).then(() => {
    console.info('Succeeded in creating pixelmap from Surface');
  }).catch((error: BusinessError) => {
    console.error(`Failed to create pixelmap. code is ${error.code}, message is ${error.message}`);
  });
}

```

