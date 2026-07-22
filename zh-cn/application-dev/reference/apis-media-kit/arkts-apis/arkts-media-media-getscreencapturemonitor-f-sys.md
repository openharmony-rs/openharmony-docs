# getScreenCaptureMonitor（系统接口）

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## getScreenCaptureMonitor

```TypeScript
function getScreenCaptureMonitor(): Promise<ScreenCaptureMonitor>
```

Obtains a **ScreenCaptureMonitor** instance. This API uses a promise to return the result.

**起始版本：** 18

<!--Device-media-function getScreenCaptureMonitor(): Promise<ScreenCaptureMonitor>--><!--Device-media-function getScreenCaptureMonitor(): Promise<ScreenCaptureMonitor>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ScreenCaptureMonitor&gt; | Promise used to return the result. The instance can be used to query and monitor the status of the system screen recorder.<br>If the operation is successful,a **ScreenCaptureMonitor** instance is returned; otherwise, **null** is returned. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [5400101](../errorcode-media.md#5400101-内存分配失败) | No memory. Return by promise. |

**示例：**

```TypeScript
let screenCaptureMonitor: media.ScreenCaptureMonitor;
try {
  screenCaptureMonitor = await media.getScreenCaptureMonitor();
} catch (err) {
  console.error(`getScreenCaptureMonitor failed, error message:${err.message}`);
}

```

