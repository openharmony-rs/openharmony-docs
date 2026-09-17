# reportAVScreenCaptureUserChoice（系统接口）

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## reportAVScreenCaptureUserChoice

```TypeScript
function reportAVScreenCaptureUserChoice(sessionId: number, choice: string): Promise<void>
```

上报录屏隐私弹窗的选择结果到ScreenCapture的服务端，用于判断是否开始录屏。如果用户选择“不允许”则不进行录屏，如果用户选择“允许”则开始录屏。使用Promise异步回调。

此接口提供给创建弹窗的系统应用调用。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sessionId | number | 是 | AVScreenCapture服务会话Id，会由AVScreenCapture拉起隐私弹窗时传给应用。 |
| choice | string | 是 | 用户的选择内容，包含是否同意录屏、选择的屏幕Id和窗口Id等。可见示例中JsonData样例。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |
| [5400101](../errorcode-media.md#5400101-内存分配失败) | No memory. Return by promise. |

**示例**

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
