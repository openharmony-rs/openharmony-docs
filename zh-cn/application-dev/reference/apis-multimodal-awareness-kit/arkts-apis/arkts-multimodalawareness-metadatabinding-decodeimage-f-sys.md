# decodeImage（系统接口）

## 导入模块

```TypeScript
import { metadataBinding } from '@kit.MultimodalAwarenessKit';
```

## decodeImage

```TypeScript
function decodeImage(encodedImage: image.PixelMap): Promise<string>
```

解析图片中携带的信息。通过对应的解码算法从图片中提取嵌入的metadata信息。使用Promise异步回调。

**起始版本：** 18

**系统能力：** SystemCapability.MultimodalAwareness.MetadataBinding

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| encodedImage | image.PixelMap | 是 | 带有信息的图片，需为通过encodeImage接口处理过的编码图片。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;string & gt; | Promise对象。返回从图片解析出的信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission check failed. A non-system application uses the system API. |
| [32100001](../errorcode-metadataBinding.md#32100001-文件创建失败) | Internal handling failed. |
| [32100003](../errorcode-metadataBinding.md#32100003-解码程序执行失败) | Decode process fail. Possible causes:  1. Image is not an encoded Image.  2. Image destroyed, decoding failed. |

**示例**

```TypeScript
import { image } from '@kit.ImageKit';
import { metadataBinding } from '@kit.MultimodalAwarenessKit';
import { BusinessError } from '@kit.BasicServicesKit';

// encodedImage需通过encodeImage接口处理后的图片获取。
let encodedImage: image.PixelMap | undefined = undefined;
let captureMetadata: string = '';
metadataBinding.decodeImage(encodedImage).then((metadata: string) => {
  // 将从图片解析出的元数据信息保存到captureMetadata变量，供后续使用
  captureMetadata = metadata;
}).catch((error: BusinessError) => {
  console.error(`Failed to decode image. Code: ${error.code}, message: ${error.message}`);
});
```
