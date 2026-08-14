# submitMetadata

## submitMetadata

```TypeScript
function submitMetadata(metadata: string): void
```

第三方应用将需要编码的内容传递给接口服务，接口服务将内容传递给调用编码接口的系统应用或服务。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-metadataBinding-function submitMetadata(metadata: string): void--><!--Device-metadataBinding-function submitMetadata(metadata: string): void-End-->

**系统能力：** SystemCapability.MultimodalAwareness.MetadataBinding

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| metadata | string | 是 | 要嵌入图片中的信息。字符串长度不超过128Bytes。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [32100001](../../apis-multimodalawareness-kit/errorcode-metadataBinding.md#32100001-文件创建失败) | Internal handling failed. |

## 示例

```TypeScript
import { metadataBinding } from '@kit.MultimodalAwarenessKit';

let metadata: string = "";
try {
  metadataBinding.submitMetadata(metadata);
} catch (error) {
  console.error("submit metadata error" + error);
}
```

