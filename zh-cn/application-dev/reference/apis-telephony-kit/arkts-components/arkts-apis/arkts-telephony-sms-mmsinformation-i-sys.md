# MmsInformation（系统接口）

彩信信息。

**起始版本：** 8

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { sms } from '@kit.TelephonyKit';
```

## attachment

```TypeScript
attachment?: Array<MmsAttachment>
```

附件

**类型：** Array&lt;[MmsAttachment](arkts-telephony-sms-mmsattachment-i-sys.md)&gt;

**起始版本：** 8

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## messageType

```TypeScript
messageType: MessageType
```

消息类型。

**类型：** [MessageType](arkts-telephony-sms-messagetype-e-sys.md)

**起始版本：** 8

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## mmsType

```TypeScript
mmsType: MmsSendReq | MmsSendConf | MmsNotificationInd | MmsRespInd | MmsRetrieveConf | MmsAcknowledgeInd | MmsDeliveryInd | MmsReadOrigInd | MmsReadRecInd
```

PDU头类型

**类型：** [MmsSendReq](arkts-telephony-sms-mmssendreq-i-sys.md) &#124; [MmsSendConf](arkts-telephony-sms-mmssendconf-i-sys.md) &#124; [MmsNotificationInd](arkts-telephony-sms-mmsnotificationind-i-sys.md) &#124; [MmsRespInd](arkts-telephony-sms-mmsrespind-i-sys.md) &#124; [MmsRetrieveConf](arkts-telephony-sms-mmsretrieveconf-i-sys.md) &#124; [MmsAcknowledgeInd](arkts-telephony-sms-mmsacknowledgeind-i-sys.md) &#124; [MmsDeliveryInd](arkts-telephony-sms-mmsdeliveryind-i-sys.md) &#124; [MmsReadOrigInd](arkts-telephony-sms-mmsreadorigind-i-sys.md) &#124; [MmsReadRecInd](arkts-telephony-sms-mmsreadrecind-i-sys.md)

**起始版本：** 8

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。
