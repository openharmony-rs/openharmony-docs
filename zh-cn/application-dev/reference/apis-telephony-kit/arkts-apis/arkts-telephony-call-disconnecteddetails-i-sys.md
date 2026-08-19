# DisconnectedDetails（系统接口）

通话结束原因。

**起始版本：** 23

<!--Device-call-export interface DisconnectedDetails--><!--Device-call-export interface DisconnectedDetails-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { call } from '@kit.TelephonyKit';
```

## message

```TypeScript
message: string
```

通话结束提示信息。

**类型：** string

**起始版本：** 23

<!--Device-DisconnectedDetails-message: string--><!--Device-DisconnectedDetails-message: string-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## reason

```TypeScript
reason: DisconnectedReason
```

通话结束原因。

**类型：** DisconnectedReason

**起始版本：** 23

<!--Device-DisconnectedDetails-reason: DisconnectedReason--><!--Device-DisconnectedDetails-reason: DisconnectedReason-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

