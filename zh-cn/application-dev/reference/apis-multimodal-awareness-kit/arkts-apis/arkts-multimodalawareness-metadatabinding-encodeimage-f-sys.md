# encodeImage（系统接口）

## 导入模块

```TypeScript
import { metadataBinding } from '@kit.MultimodalAwarenessKit';
```

## encodeImage

```TypeScript
function encodeImage(srcImage: image.PixelMap, metadata: string): Promise<image.PixelMap>
```

在图片中加入信息。通过特定的编码算法将metadata信息嵌入到图片中，编码过程对图片的视觉呈现影响极小，嵌入的信息可通过decodeImage接口解析。可用于防伪、版权保护等场景。 使用Promise异步回调。

**起始版本：** 18

**系统能力：** SystemCapability.MultimodalAwareness.MetadataBinding

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| srcImage | image.PixelMap | 是 | 待编码的原始图片，用于嵌入metadata信息。 |
| metadata | string | 是 | 嵌入的信息。字符串编码格式建议使用UTF-8，长度不应超过128Bytes，且避免包含不可打印字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;image.PixelMap & gt; | Promise对象。返回嵌入信息的图片。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission check failed. A non-system application uses the system API. |
| [32100001](../errorcode-metadataBinding.md#32100001-文件创建失败) | Internal handling failed. |
| [32100002](../errorcode-metadataBinding.md#32100002-编码程序执行失败) | Encode process fail. Possible causes:  1. Image processing error.  2. Channel coding error. |

**示例**

```TypeScript
import { image } from '@kit.ImageKit';
import { metadataBinding } from '@kit.MultimodalAwarenessKit';
import { BusinessError } from '@kit.BasicServicesKit';

let encodedImage: image.PixelMap | undefined = undefined;
let metadata: string = '';
// srcImage需通过image内的接口获取有效的PixelMap对象
let srcImage: image.PixelMap | undefined = undefined;
metadataBinding.encodeImage(srcImage, metadata).then((pixelMap: image.PixelMap) => {
  encodedImage = pixelMap;
}).catch((error: BusinessError) => {
  console.error(`Failed to encode image. Code: ${error.code}, message: ${error.message}`);
});
```
