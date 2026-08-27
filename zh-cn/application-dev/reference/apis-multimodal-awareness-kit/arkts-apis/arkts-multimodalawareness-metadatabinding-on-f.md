# on

## 导入模块

```TypeScript
import { metadataBinding } from '@kit.MultimodalAwarenessKit';
```

## on('operationSubmitMetadata')

```TypeScript
function on(type: 'operationSubmitMetadata', bundleName: string, callback: Callback<number>): void
```

订阅系统应用请求获取编码内容的事件。当系统应用（如截图）请求获取应用的编码内容时触发该事件，应用注册回调后，事件发生时通过回调通知应用。调用on()方法订阅事件后， 必须在不再需要监听事件时调用off()方法取消订阅，释放监听资源。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.MultimodalAwareness.MetadataBinding

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'operationSubmitMetadata' | 是 | 事件类型，固定传入'operationSubmitMetadata'，表示系统应用获取编码内容。 |
| bundleName | string | 是 | 应用包名，用于标识注册订阅事件的第三方应用。在事件发生时，系统将通过此包名识别并通知对应的注册应用。需确保传入的包名为有效的应用包名。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 是 | 回调函数，用于返回事件码。当事件值为1时表示截图事件，目前仅支持截图事件，取值范围：1（截图事件）。注意：回调函数应快速执行， 避免阻塞UI线程。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [32100001](../errorcode-metadataBinding.md#32100001-文件创建失败) | Internal handling failed. |
| [32100004](../errorcode-metadataBinding.md#32100004-订阅失败) | Subscribe Failed. Possible causes:  1. Abnormal system capability.  2. IPC communication abnormality.  3. Algorithm loading exception. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { metadataBinding } from '@kit.MultimodalAwarenessKit';

let bundleName: string = 'com.example.app';
try {
  metadataBinding.on('operationSubmitMetadata', bundleName, (event: number) => {
    if (event == 1) {
      console.info('The screenshot request is received and the app link is obtained');
    }
  });
} catch (error) {
  const err = error as BusinessError;
  console.error(`Failed to register operationSubmitMetadata event. Code: ${err.code}, message: ${err.message}`);
}
```
