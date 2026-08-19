# MmsInformation（系统接口）

彩信信息。

**起始版本：** 23

<!--Device-sms-export interface MmsInformation--><!--Device-sms-export interface MmsInformation-End-->

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

**起始版本：** 23

<!--Device-MmsInformation-attachment?: Array<MmsAttachment>--><!--Device-MmsInformation-attachment?: Array<MmsAttachment>-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## messageType

```TypeScript
messageType: MessageType
```

消息类型。

**类型：** MessageType

**起始版本：** 23

<!--Device-MmsInformation-messageType: MessageType--><!--Device-MmsInformation-messageType: MessageType-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## mmsType

```TypeScript
mmsType: MmsSendReq | MmsSendConf | MmsNotificationInd | MmsRespInd | MmsRetrieveConf | MmsAcknowledgeInd | MmsDeliveryInd | MmsReadOrigInd | MmsReadRecInd
```

PDU头类型

**类型：** [MmsSendReq](arkts-telephony-sms-mmssendreq-i-sys.md) \| [MmsSendConf](arkts-telephony-sms-mmssendconf-i-sys.md) \| [MmsNotificationInd](arkts-telephony-sms-mmsnotificationind-i-sys.md) \| [MmsRespInd](arkts-telephony-sms-mmsrespind-i-sys.md) \| [MmsRetrieveConf](arkts-telephony-sms-mmsretrieveconf-i-sys.md) \| [MmsAcknowledgeInd](arkts-telephony-sms-mmsacknowledgeind-i-sys.md) \| [MmsDeliveryInd](arkts-telephony-sms-mmsdeliveryind-i-sys.md) \| [MmsReadOrigInd](arkts-telephony-sms-mmsreadorigind-i-sys.md) \| [MmsReadRecInd](arkts-telephony-sms-mmsreadrecind-i-sys.md)

**起始版本：** 23

<!--Device-MmsInformation-mmsType: MmsSendReq | MmsSendConf | MmsNotificationInd | MmsRespInd | MmsRetrieveConf | MmsAcknowledgeInd | MmsDeliveryInd | MmsReadOrigInd | MmsReadRecInd--><!--Device-MmsInformation-mmsType: MmsSendReq | MmsSendConf | MmsNotificationInd | MmsRespInd | MmsRetrieveConf | MmsAcknowledgeInd | MmsDeliveryInd | MmsReadOrigInd | MmsReadRecInd-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

