# @ohos.telephony.sms(SMS)

The **sms** module provides basic SMS management functions. With the APIs provided by this module, you can create and send SMS messages, and obtain the ID of the default SIM card used to send and receive SMS messages, and check whether the current device can send and receive SMS messages.

**Since:** 6

**System capability:** SystemCapability.Telephony.SmsMms

## Modules to Import

```TypeScript
import { sms } from '@kit.TelephonyKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [createMessage](arkts-telephony-sms-createmessage-f.md) | Creates an SMS instance based on the protocol data unit (PDU) and specified SMS protocol. This API uses an asynchronous callback to return the result. |
| [createMessage](arkts-telephony-sms-createmessage-f.md) | Creates an SMS instance based on the protocol data unit (PDU) and specified SMS protocol. This API uses a promise to return the result. |
| [getDefaultSmsSimId](arkts-telephony-sms-getdefaultsmssimid-f.md) | Obtains the default ID of the SIM card used to send SMS messages. This API uses an asynchronous callback to return the result. |
| [getDefaultSmsSimId](arkts-telephony-sms-getdefaultsmssimid-f.md) | Obtains the default ID of the SIM card used to send SMS messages. This API uses a promise to return the result. |
| [getDefaultSmsSlotId](arkts-telephony-sms-getdefaultsmsslotid-f.md) | Obtains the default slot ID of the SIM card used to send SMS messages. This API uses an asynchronous callback to return the result. |
| [getDefaultSmsSlotId](arkts-telephony-sms-getdefaultsmsslotid-f.md) | Obtains the default slot ID of the SIM card used to send SMS messages. This API uses a promise to return the result. |
| [hasSmsCapability](arkts-telephony-sms-hassmscapability-f.md) | Checks whether the current device can send and receive SMS messages. This API works in synchronous mode. |
| [sendMessage](arkts-telephony-sms-sendmessage-f.md) | Sends an SMS message. |
| [sendShortMessage](arkts-telephony-sms-sendshortmessage-f.md) | Sends an SMS message. This API uses an asynchronous callback to return the result. |
| [sendShortMessage](arkts-telephony-sms-sendshortmessage-f.md) | Sends an SMS message. This API uses a promise to return the result. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [addSimMessage](arkts-telephony-sms-addsimmessage-f-sys.md) | Adds a message to the SIM card. If the SIM card is full, an error is reported. This API uses an asynchronous callback to return the result. |
| [addSimMessage](arkts-telephony-sms-addsimmessage-f-sys.md) | Adds a message to the SIM card. If the SIM card is full, an error is reported. This API uses a promise to return the result. |
| [decodeMms](arkts-telephony-sms-decodemms-f-sys.md) | Decodes MMS messages. This API uses an asynchronous callback to return the result. |
| [decodeMms](arkts-telephony-sms-decodemms-f-sys.md) | Decodes MMS messages. This API uses a promise to return the result. |
| [delSimMessage](arkts-telephony-sms-delsimmessage-f-sys.md) | Deletes a message from the SIM card. If the specified **msgIndex** is invalid, an error is reported. This API uses an asynchronous callback to return the result. |
| [delSimMessage](arkts-telephony-sms-delsimmessage-f-sys.md) | Deletes a message from the SIM card. If the specified **msgIndex** is invalid, an error is reported. This API uses a promise to return the result. |
| [downloadMms](arkts-telephony-sms-downloadmms-f-sys.md) | Downloads an MMS message. This API uses an asynchronous callback to return the result. |
| [downloadMms](arkts-telephony-sms-downloadmms-f-sys.md) | Downloads an MMS message. This API uses a promise to return the result. |
| [encodeMms](arkts-telephony-sms-encodemms-f-sys.md) | MMS message code. This API uses an asynchronous callback to return the result. |
| [encodeMms](arkts-telephony-sms-encodemms-f-sys.md) | MMS message code. This API uses a promise to return the result. |
| [getAllSimMessages](arkts-telephony-sms-getallsimmessages-f-sys.md) | Obtains all SIM card messages. This API uses an asynchronous callback to return the result. |
| [getAllSimMessages](arkts-telephony-sms-getallsimmessages-f-sys.md) | Obtains all SIM card messages. This API uses a promise to return the result. |
| [getImsShortMessageFormat](arkts-telephony-sms-getimsshortmessageformat-f-sys.md) | Obtains the SMS format supported by the IMS, for example, **3gpp**, **3gpp2**, or **unknown**. This API uses an asynchronous callback to return the result. |
| [getImsShortMessageFormat](arkts-telephony-sms-getimsshortmessageformat-f-sys.md) | Obtains the SMS format supported by the IMS, for example, **3gpp**, **3gpp2**, or **unknown**. This API uses a promise to return the result. |
| [getSmscAddr](arkts-telephony-sms-getsmscaddr-f-sys.md) | Obtains the SMSC address. This API uses an asynchronous callback to return the result. |
| [getSmscAddr](arkts-telephony-sms-getsmscaddr-f-sys.md) | Obtains the SMSC address. This API uses a promise to return the result. |
| [getSmsSegmentsInfo](arkts-telephony-sms-getsmssegmentsinfo-f-sys.md) | Obtains SMS message segment information. This API uses an asynchronous callback to return the result. |
| [getSmsSegmentsInfo](arkts-telephony-sms-getsmssegmentsinfo-f-sys.md) | Obtains SMS message segment information. This API uses a promise to return the result. |
| [getSmsShortCodeType](arkts-telephony-sms-getsmsshortcodetype-f-sys.md) | Get the SMS short code type of the destination address. |
| [isImsSmsSupported](arkts-telephony-sms-isimssmssupported-f-sys.md) | Checks whether SMS is supported on IMS. This API uses an asynchronous callback to return the result. |
| [isImsSmsSupported](arkts-telephony-sms-isimssmssupported-f-sys.md) | Checks whether SMS is supported on IMS. This API uses a promise to return the result. |
| [sendMms](arkts-telephony-sms-sendmms-f-sys.md) | Sends an MMS message. This API uses an asynchronous callback to return the result. |
| [sendMms](arkts-telephony-sms-sendmms-f-sys.md) | Sends an MMS message. This API uses a promise to return the result. |
| [setCBConfig](arkts-telephony-sms-setcbconfig-f-sys.md) | Sets the cell broadcast configuration. This API uses an asynchronous callback to return the result. |
| [setCBConfig](arkts-telephony-sms-setcbconfig-f-sys.md) | Sets the cell broadcast configuration. This API uses a promise to return the result. |
| [setCBConfigList](arkts-telephony-sms-setcbconfiglist-f-sys.md) | Turn on Cell BroadCast by list. |
| [setDefaultSmsSlotId](arkts-telephony-sms-setdefaultsmsslotid-f-sys.md) | Sets the default slot ID of the SIM card used to send SMS messages. This API uses an asynchronous callback to return the result. |
| [setDefaultSmsSlotId](arkts-telephony-sms-setdefaultsmsslotid-f-sys.md) | Sets the default slot ID of the SIM card used to send SMS messages. This API uses a promise to return the result. |
| [setSmscAddr](arkts-telephony-sms-setsmscaddr-f-sys.md) | Sets the short message service center (SMSC) address. This API uses an asynchronous callback to return the result. |
| [setSmscAddr](arkts-telephony-sms-setsmscaddr-f-sys.md) | Sets the SMSC address. This API uses a promise to return the result. |
| [splitMessage](arkts-telephony-sms-splitmessage-f-sys.md) | Splits an SMS message into multiple segments. This API uses an asynchronous callback to return the result. |
| [splitMessage](arkts-telephony-sms-splitmessage-f-sys.md) | Splits an SMS message into multiple segments. This API uses a promise to return the result. |
| [updateSimMessage](arkts-telephony-sms-updatesimmessage-f-sys.md) | Updates a SIM message. This API uses an asynchronous callback to return the result. |
| [updateSimMessage](arkts-telephony-sms-updatesimmessage-f-sys.md) | Updates a SIM message. This API uses a promise to return the result. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [IDeliveryShortMessageCallback](arkts-telephony-sms-ideliveryshortmessagecallback-i.md) | Provides the callback for the SMS message delivery report. |
| [ISendShortMessageCallback](arkts-telephony-sms-isendshortmessagecallback-i.md) | Provides the callback for the SMS message sending result. It consists of three parts: SMS message sending result, URI for storing the sent SMS message, and whether the SMS message is the last part of a long SMS message. |
| [SendMessageOptions](arkts-telephony-sms-sendmessageoptions-i.md) | Provides the options (including callbacks) for sending SMS messages. For example, you can specify the SMS message type by the optional parameter **content**. |
| [ShortMessage](arkts-telephony-sms-shortmessage-i.md) | Defines an SMS message instance. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [CBConfigListConfigs](arkts-telephony-sms-cbconfiglistconfigs-i-sys.md) | Defines the cell broadcast configuration list configs. |
| [CBConfigOptions](arkts-telephony-sms-cbconfigoptions-i-sys.md) | Defines the cell broadcast configuration options. |
| [MmsAcknowledgeInd](arkts-telephony-sms-mmsacknowledgeind-i-sys.md) | Defines an MMS confirmation index. |
| [MmsAddress](arkts-telephony-sms-mmsaddress-i-sys.md) | Defines an MMSC address. |
| [MmsAttachment](arkts-telephony-sms-mmsattachment-i-sys.md) | Defines the attachment of an MMS message. |
| [MmsConfig](arkts-telephony-sms-mmsconfig-i-sys.md) | MMS configuration file. |
| [MmsDeliveryInd](arkts-telephony-sms-mmsdeliveryind-i-sys.md) | Defines an MMS message delivery index. |
| [MmsInformation](arkts-telephony-sms-mmsinformation-i-sys.md) | Defines the MMS message information. |
| [MmsNotificationInd](arkts-telephony-sms-mmsnotificationind-i-sys.md) | Defines an MMS notification index. |
| [MmsParams](arkts-telephony-sms-mmsparams-i-sys.md) | Defines the parameters for sending SMS messages. |
| [MmsReadOrigInd](arkts-telephony-sms-mmsreadorigind-i-sys.md) | Defines the original MMS message reading index. |
| [MmsReadRecInd](arkts-telephony-sms-mmsreadrecind-i-sys.md) | Defines the MMS message reading index. |
| [MmsRespInd](arkts-telephony-sms-mmsrespind-i-sys.md) | Defines an MMS response index. |
| [MmsRetrieveConf](arkts-telephony-sms-mmsretrieveconf-i-sys.md) | Defines the MMS message retrieval configuration. |
| [MmsSendConf](arkts-telephony-sms-mmssendconf-i-sys.md) | Defines the MMS message sending configuration. |
| [MmsSendReq](arkts-telephony-sms-mmssendreq-i-sys.md) | Defines an MMS message sending request. |
| [SimMessageOptions](arkts-telephony-sms-simmessageoptions-i-sys.md) | Defines the SIM message options. |
| [SimShortMessage](arkts-telephony-sms-simshortmessage-i-sys.md) | Defines a SIM message. |
| [SmsSegmentsInfo](arkts-telephony-sms-smssegmentsinfo-i-sys.md) | Defines the SMS message segment information. |
| [UpdateSimMessageOptions](arkts-telephony-sms-updatesimmessageoptions-i-sys.md) | Defines the updating SIM message options. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [SendSmsResult](arkts-telephony-sms-sendsmsresult-e.md) | Enumerates SMS message sending results. |
| [ShortMessageClass](arkts-telephony-sms-shortmessageclass-e.md) | Enumerates SMS message types. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [DispositionType](arkts-telephony-sms-dispositiontype-e-sys.md) | Enumerates disposition types. |
| [MessageType](arkts-telephony-sms-messagetype-e-sys.md) | Message type. |
| [MmsCharSets](arkts-telephony-sms-mmscharsets-e-sys.md) | Enumerates MMS character sets. |
| [MmsPriorityType](arkts-telephony-sms-mmsprioritytype-e-sys.md) | Enumerates MMS message priorities. |
| [MmsVersionType](arkts-telephony-sms-mmsversiontype-e-sys.md) | Enumerates MMS versions. |
| [RanType](arkts-telephony-sms-rantype-e-sys.md) | RAN type. |
| [ReportType](arkts-telephony-sms-reporttype-e-sys.md) | Enumerates report types. |
| [SimMessageStatus](arkts-telephony-sms-simmessagestatus-e-sys.md) | Defines the SIM message status. |
| [SmsEncodingScheme](arkts-telephony-sms-smsencodingscheme-e-sys.md) | Enumerates SMS encoding schemes. |
| [SmsShortCodeType](arkts-telephony-sms-smsshortcodetype-e-sys.md) | Enumerates SMS short code types. |
<!--DelEnd-->
