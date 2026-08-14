# getAVScreenCaptureConfigurableParameters（系统接口）

## getAVScreenCaptureConfigurableParameters

```TypeScript
function getAVScreenCaptureConfigurableParameters(sessionId: int): Promise<string>
```

get Configurations which user can changes from AVScreenCapture server

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-media-function getAVScreenCaptureConfigurableParameters(sessionId: int): Promise<string>--><!--Device-media-function getAVScreenCaptureConfigurableParameters(sessionId: int): Promise<string>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sessionId | int | 是 | The AVScreenCapture server session ID. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Returns a configurable configuration item string. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called from Non-System applications. Return by promise. |
| [5400109](../errorcode-media.md#5400109-会话id不存在) | Sessions not exist. Return by promise. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';

let sessionId: number = 0; // 替换成拉起此进程的sessionId。

try {
  let privacyResult: string = await media.getAVScreenCaptureConfigurableParameters(sessionId);
} catch (error: BusinessError) {
  console.error(`getAVScreenCaptureConfigurableParameters error, error message: ${error.message}`);
}
```

