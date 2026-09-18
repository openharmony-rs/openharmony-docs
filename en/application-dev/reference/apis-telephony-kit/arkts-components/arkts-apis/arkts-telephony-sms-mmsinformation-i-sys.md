# MmsInformation (System API)

Defines the MMS message information.

**Since:** 8

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { sms } from '@kit.TelephonyKit';
```

## attachment

```TypeScript
attachment?: Array<MmsAttachment>
```

Attachment.

**Type:** Array&lt;[MmsAttachment](arkts-telephony-sms-mmsattachment-i-sys.md)&gt;

**Since:** 8

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## messageType

```TypeScript
messageType: MessageType
```

Message type.

**Type:** [MessageType](arkts-telephony-sms-messagetype-e-sys.md)

**Since:** 8

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

## mmsType

```TypeScript
mmsType: MmsSendReq | MmsSendConf | MmsNotificationInd | MmsRespInd | MmsRetrieveConf | MmsAcknowledgeInd | MmsDeliveryInd | MmsReadOrigInd | MmsReadRecInd
```

PDU header type.

**Type:** [MmsSendReq](arkts-telephony-sms-mmssendreq-i-sys.md) &#124; [MmsSendConf](arkts-telephony-sms-mmssendconf-i-sys.md) &#124; [MmsNotificationInd](arkts-telephony-sms-mmsnotificationind-i-sys.md) &#124; [MmsRespInd](arkts-telephony-sms-mmsrespind-i-sys.md) &#124; [MmsRetrieveConf](arkts-telephony-sms-mmsretrieveconf-i-sys.md) &#124; [MmsAcknowledgeInd](arkts-telephony-sms-mmsacknowledgeind-i-sys.md) &#124; [MmsDeliveryInd](arkts-telephony-sms-mmsdeliveryind-i-sys.md) &#124; [MmsReadOrigInd](arkts-telephony-sms-mmsreadorigind-i-sys.md) &#124; [MmsReadRecInd](arkts-telephony-sms-mmsreadrecind-i-sys.md)

**Since:** 8

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.
