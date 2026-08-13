# offOperationSubmitMetadata

## offOperationSubmitMetadata

```TypeScript
function offOperationSubmitMetadata(bundleName: string, callback?: Callback<int>): void
```

取消订阅系统获取编码内容的事件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-metadataBinding-function offOperationSubmitMetadata(bundleName: string, callback?: Callback<int>): void--><!--Device-metadataBinding-function offOperationSubmitMetadata(bundleName: string, callback?: Callback<int>): void-End-->

**系统能力：** SystemCapability.MultimodalAwareness.MetadataBinding

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 第三方应用的包名，需与订阅时传入的包名一致。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;int&gt; | 否 | 回调函数，返回截图事件。需要取消监听的回调函数，需与订阅时传入的回调函数一致。若不填，则取消当前监听该事件的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [32100001](../../apis-multimodalawareness-kit/errorcode-metadataBinding.md#32100001-文件创建失败) | Internal handling failed. |
| [32100005](../../apis-multimodalawareness-kit/errorcode-metadataBinding.md#32100005-取消订阅失败) | Unsubscribe Failed. Possible causes: &lt;br&gt;1. Abnormal system capability. &lt;br&gt;2. IPC communication abnormality. |

## 示例

```TypeScript
import { metadataBinding } from '@kit.MultimodalAwarenessKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName: string = '';
try {
  metadataBinding.offOperationSubmitMetadata(bundleName, (event: int)=>{});
} catch (error) {
  console.error("Unsubscribe screenshot event" + error);
}
```

