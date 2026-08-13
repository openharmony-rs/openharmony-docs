# onAttachmentDidFail

## onAttachmentDidFail

```TypeScript
function onAttachmentDidFail(callback: Callback<AttachFailureReason>): void
```

订阅绑定失败事件。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-inputMethod-function onAttachmentDidFail(callback: Callback<AttachFailureReason>): void--><!--Device-inputMethod-function onAttachmentDidFail(callback: Callback<AttachFailureReason>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AttachFailureReason](arkts-ime-inputmethod-attachfailurereason-e.md)&gt; | 是 | 回调函数，返回绑定失败的原因，仅当注册者进程触发的绑定失败时，调用该回调函数。 |

## 示例

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

let attachmentDidFailCallback: Callback<inputMethod.AttachFailureReason> = 
  (reason: inputMethod.AttachFailureReason): void => {
    console.info(`Attachment failed with reason: ${reason}.`);
  if (reason === inputMethod.AttachFailureReason.CALLER_NOT_FOCUSED) {
    console.info(`Failure reason is CALLER_NOT_FOCUSED.`);
  }
  };
inputMethod.onAttachmentDidFail(attachmentDidFailCallback);
```

