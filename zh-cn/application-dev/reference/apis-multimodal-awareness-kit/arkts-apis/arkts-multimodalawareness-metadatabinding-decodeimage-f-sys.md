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

**起始版本：** 23

<!--Device-metadataBinding-function decodeImage(encodedImage: image.PixelMap): Promise<string>--><!--Device-metadataBinding-function decodeImage(encodedImage: image.PixelMap): Promise<string>-End-->

**系统能力：** SystemCapability.MultimodalAwareness.MetadataBinding

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| encodedImage | image.PixelMap | 是 | 带有信息的图片，需为通过encodeImage接口处理过的编码图片。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象。返回从图片解析出的信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [32100001](../../apis-multimodalawareness-kit/errorcode-metadataBinding.md#32100001-文件创建失败) | Internal handling failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission check failed. A non-system application uses the system API. |
| [32100003](../../apis-multimodalawareness-kit/errorcode-metadataBinding.md#32100003-解码程序执行失败) | Decode process fail. Possible causes: <br>1. Image is not an encoded Image. <br>2. Image destroyed, decoding failed. |

