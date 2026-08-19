# offRotationAxesStatusChange（系统接口）

## 导入模块

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

## offRotationAxesStatusChange

```TypeScript
function offRotationAxesStatusChange(callback?: Callback<RotationAxesStateChangeInfo>): void
```

Unregister a listener for axis state changes.

**起始版本：** 23

<!--Device-mechanicManager-function offRotationAxesStatusChange(callback?: Callback<RotationAxesStateChangeInfo>): void--><!--Device-mechanicManager-function offRotationAxesStatusChange(callback?: Callback<RotationAxesStateChangeInfo>): void-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[RotationAxesStateChangeInfo](arkts-mechanic-mechanicmanager-rotationaxesstatechangeinfo-i-sys.md)&gt; | 否 | Rotate axis state changes callback. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [33300001](../errorcode-mechanic.md#33300001-系统错误) | Service exception. |

