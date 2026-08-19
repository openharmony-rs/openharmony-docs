# UpdateSimMessageOptions（系统接口）

更新SIM卡消息选项。

**起始版本：** 23

<!--Device-sms-export interface UpdateSimMessageOptions--><!--Device-sms-export interface UpdateSimMessageOptions-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { sms } from '@kit.TelephonyKit';
```

## msgIndex

```TypeScript
msgIndex: int
```

消息索引

**类型：** int

**起始版本：** 23

<!--Device-UpdateSimMessageOptions-msgIndex: int--><!--Device-UpdateSimMessageOptions-msgIndex: int-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## newStatus

```TypeScript
newStatus: SimMessageStatus
```

新状态

**类型：** [SimMessageStatus](arkts-telephony-sms-simmessagestatus-e-sys.md)

**起始版本：** 23

<!--Device-UpdateSimMessageOptions-newStatus: SimMessageStatus--><!--Device-UpdateSimMessageOptions-newStatus: SimMessageStatus-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## pdu

```TypeScript
pdu: string
```

协议数据单元

**类型：** string

**起始版本：** 23

<!--Device-UpdateSimMessageOptions-pdu: string--><!--Device-UpdateSimMessageOptions-pdu: string-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## slotId

```TypeScript
slotId: int
```

卡槽ID

**类型：** int

**起始版本：** 23

<!--Device-UpdateSimMessageOptions-slotId: int--><!--Device-UpdateSimMessageOptions-slotId: int-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## smsc

```TypeScript
smsc: string
```

短消息业务中心

**类型：** string

**起始版本：** 23

<!--Device-UpdateSimMessageOptions-smsc: string--><!--Device-UpdateSimMessageOptions-smsc: string-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

