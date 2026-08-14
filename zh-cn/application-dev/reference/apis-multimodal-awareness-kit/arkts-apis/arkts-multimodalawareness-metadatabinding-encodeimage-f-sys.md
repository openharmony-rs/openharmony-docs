# encodeImage（系统接口）

## encodeImage

```TypeScript
function encodeImage(srcImage: image.PixelMap, metadata: string): Promise<image.PixelMap>
```

在图片中加入信息。通过特定的编码算法将metadata信息嵌入到图片中。可用于防伪、版权保护等场景。使用promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-metadataBinding-function encodeImage(srcImage: image.PixelMap, metadata: string): Promise<image.PixelMap>--><!--Device-metadataBinding-function encodeImage(srcImage: image.PixelMap, metadata: string): Promise<image.PixelMap>-End-->

**系统能力：** SystemCapability.MultimodalAwareness.MetadataBinding

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| srcImage | image.PixelMap | 是 | 待编码的原始图片，用于嵌入metadata信息的图片。 |
| metadata | string | 是 | 嵌入的信息。字符串编码格式建议使用UTF-8，长度不应超过128Bytes，且避免包含不可打印字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;image.PixelMap&gt; | Promise对象。返回嵌入信息的图片。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [32100001](../../apis-multimodalawareness-kit/errorcode-metadataBinding.md#32100001-文件创建失败) | Internal handling failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission check failed. A non-system application uses the system API. |
| [32100002](../../apis-multimodalawareness-kit/errorcode-metadataBinding.md#32100002-编码程序执行失败) | Encode process fail. Possible causes: &lt;br&gt;1. Image processing error. &lt;br&gt;2. Channel coding error. |

