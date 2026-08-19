# onCaptureStatusChange

## 导入模块

```TypeScript
import { display } from '@kit.ArkUI';
```

## onCaptureStatusChange

```TypeScript
function onCaptureStatusChange(callback: Callback<boolean>): void
```

Register the callback for device capture, casting, or recording status changes.

**起始版本：** 23

<!--Device-display-function onCaptureStatusChange(callback: Callback<boolean>): void--><!--Device-display-function onCaptureStatusChange(callback: Callback<boolean>): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;boolean&gt; | 是 | Callback used to return the device capture, casting, or recording status. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1400003](../errorcode-display.md#1400003-系统服务工作异常) | This display manager service works abnormally. |

**示例**

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

let callback: Callback<boolean> = (captureStatus: boolean) => {
  console.info(`Listening capture status: ${captureStatus}`);
};
display.onCaptureStatusChange(callback);
```

