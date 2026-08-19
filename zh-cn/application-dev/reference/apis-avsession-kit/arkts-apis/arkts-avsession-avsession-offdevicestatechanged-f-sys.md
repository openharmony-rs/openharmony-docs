# offDeviceStateChanged（系统接口）

## 导入模块

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## offDeviceStateChanged

```TypeScript
function offDeviceStateChanged(callback?: Callback<DeviceState>): void
```

Unregisters a system callback for the device connection phase.

**起始版本：** 23

**需要权限：** ohos.permission.MANAGE_MEDIA_RESOURCES

<!--Device-avSession-function offDeviceStateChanged(callback?: Callback<DeviceState>): void--><!--Device-avSession-function offDeviceStateChanged(callback?: Callback<DeviceState>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[DeviceState](arkts-avsession-avsession-devicestate-i-sys.md)&gt; | 否 | Callback used to return the device information. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |

