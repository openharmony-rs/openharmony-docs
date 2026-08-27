# off

## 导入模块

```TypeScript
import { metadataBinding } from '@kit.MultimodalAwarenessKit';
```

## off('operationSubmitMetadata')

```TypeScript
function off(type: 'operationSubmitMetadata', bundleName: string, callback?: Callback<number>): void
```

取消订阅系统获取编码内容的事件。需先调用on('operationSubmitMetadata')方法订阅事件，未订阅时调用不产生效果。取消订阅后，应用将不再接收编码内容传递事件。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.MultimodalAwareness.MetadataBinding

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'operationSubmitMetadata' | 是 | 事件类型，固定传入'operationSubmitMetadata'，表示系统应用获取编码内容。 |
| bundleName | string | 是 | 应用包名，标识注册应用的包名，需与订阅时传入的包名一致。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 否 | 回调函数，用于返回事件码。需要取消监听的回调函数，需与订阅时传入的回调函数一致。建议在订阅时保存回调函数引用， 在取消订阅时使用同一引用。若不填，则取消当前监听该事件的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [32100001](../errorcode-metadataBinding.md#32100001-文件创建失败) | Internal handling failed. |
| [32100005](../errorcode-metadataBinding.md#32100005-取消订阅失败) | Unsubscribe Failed. Possible causes:   1. Abnormal system capability.   2. IPC communication abnormality. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { metadataBinding } from '@kit.MultimodalAwarenessKit';

let bundleName: string = 'com.example.app';
try {
  metadataBinding.off('operationSubmitMetadata', bundleName);
} catch (error) {
 const err = error as BusinessError;
 console.error(`Failed to unsubscribe operationSubmitMetadata event. Code: ${err.code}, message: ${err.message}`);
}
```
