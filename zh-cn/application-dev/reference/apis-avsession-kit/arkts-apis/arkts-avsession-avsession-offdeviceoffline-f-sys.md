# offDeviceOffline（系统接口）

## 导入模块

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## offDeviceOffline

```TypeScript
function offDeviceOffline(callback?: Callback<string>): void
```

Unregister device offline callback

**起始版本：** 23

<!--Device-avSession-function offDeviceOffline(callback?: Callback<string>): void--><!--Device-avSession-function offDeviceOffline(callback?: Callback<string>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;string&gt; | 否 | Used to returns the device info |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |

**示例**

```TypeScript
avSession.offDeviceOffline();
```

