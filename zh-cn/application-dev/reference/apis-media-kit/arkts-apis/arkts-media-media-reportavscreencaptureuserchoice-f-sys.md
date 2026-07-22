# reportAVScreenCaptureUserChoice（系统接口）

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## reportAVScreenCaptureUserChoice

```TypeScript
function reportAVScreenCaptureUserChoice(sessionId: number, choice: string): Promise<void>
```

Reports the user selection result in the screen capture privacy dialog box to the AVScreenCapture server to determine whether to start screen capture. Screen capture starts only when the user touches a button to continue the operation.This API is called by the system application that creates the dialog box.

**起始版本：** 12

<!--Device-media-function reportAVScreenCaptureUserChoice(sessionId: int, choice: string): Promise<void>--><!--Device-media-function reportAVScreenCaptureUserChoice(sessionId: int, choice: string): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sessionId | number | 是 | Session ID of the AVScreenCapture service, which is sent to the application when |
| choice | string | 是 | User choice, including whether screen capture is agreed, selected display ID, |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. 3.Parameter verification failed. |
| [5400101](../errorcode-media.md#5400101-内存分配失败) | No memory. Return by promise. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';

class JsonData {
  public choice: string = 'true';
  public displayId: number | null = -1;
  public missionId: number | null = -1;
  public checkBoxSelected: string = 'true';
  public isInnerAudioBoxSelected: string = 'true';
}
let sessionId: number = 0; // 替换成拉起此进程的sessionId。

try {
  const jsonData: JsonData = {
    choice: 'true',  // 替换成用户的选择内容。
    displayId: -1,   // 替换成用户选择的屏幕Id。
    missionId: -1,   // 替换成用户选择的窗口Id。
    checkBoxSelected: 'true',   // 替换成用户是否开启屏幕保护。
    isInnerAudioBoxSelected: 'true',   // 替换成用户是否开启内部音频录制。
  }
  await media.reportAVScreenCaptureUserChoice(sessionId, JSON.stringify(jsonData));
} catch (error: BusinessError) {
  console.error(`reportAVScreenCaptureUserChoice error, error message: ${error.message}`);
}

```

