# @ohos.telephony.sms

短信服务提供了管理短信的一些基础能力，包括创建、发送短信，获取发送短信的默认SIM卡槽ID、检查当前设备是否具备短信发送和接收能力等。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare namespace sms--><!--Device-unnamed-declare namespace sms-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createMessage](arkts-telephony-sms-createmessage-f.md#createMessage) | 根据协议数据单元(PDU)和指定的短信协议创建短信实例。使用callback异步回调。 |
| [createMessage](arkts-telephony-sms-createmessage-f.md#createMessage) | 根据协议数据单元(PDU)和指定的短信协议创建短信实例。使用Promise异步回调。 |
| [getDefaultSmsSimId](arkts-telephony-sms-getdefaultsmssimid-f.md#getDefaultSmsSimId) | 获取发送短信的默认SIM卡ID。使用callback异步回调。 |
| [getDefaultSmsSimId](arkts-telephony-sms-getdefaultsmssimid-f.md#getDefaultSmsSimId) | 获取发送短信的默认SIM卡ID。使用Promise异步回调。 |
| [getDefaultSmsSlotId](arkts-telephony-sms-getdefaultsmsslotid-f.md#getDefaultSmsSlotId) | 获取发送短信的默认SIM卡槽ID。使用callback异步回调。 |
| [getDefaultSmsSlotId](arkts-telephony-sms-getdefaultsmsslotid-f.md#getDefaultSmsSlotId) | 获取发送短信的默认SIM卡槽ID。使用Promise异步回调。 |
| [hasSmsCapability](arkts-telephony-sms-hassmscapability-f.md#hasSmsCapability) | 检查当前设备是否具备短信发送和接收能力，该方法是同步方法。 |
| [sendMessage](arkts-telephony-sms-sendmessage-f.md#sendMessage) | 发送短信。 |
| [sendShortMessage](arkts-telephony-sms-sendshortmessage-f.md#sendShortMessage) | 发送短信。使用callback异步回调。 |
| [sendShortMessage](arkts-telephony-sms-sendshortmessage-f.md#sendShortMessage) | 发送短信。使用Promise异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [addSimMessage](arkts-telephony-sms-addsimmessage-f-sys.md#addSimMessage) | 添加SIM卡消息，sim卡消息满，添加报错。使用callback异步回调。 |
| [addSimMessage](arkts-telephony-sms-addsimmessage-f-sys.md#addSimMessage（系统接口）) | 添加SIM卡消息，sim卡消息满，添加报错。使用Promise异步回调。 |
| [decodeMms](arkts-telephony-sms-decodemms-f-sys.md#decodeMms) | 彩信解码。使用callback异步回调。 |
| [decodeMms](arkts-telephony-sms-decodemms-f-sys.md#decodeMms（系统接口）) | 彩信解码。使用Promise异步回调。 |
| [delSimMessage](arkts-telephony-sms-delsimmessage-f-sys.md#delSimMessage) | 删除SIM卡消息，msgIndex无效时，删除报错。使用callback异步回调。 |
| [delSimMessage](arkts-telephony-sms-delsimmessage-f-sys.md#delSimMessage（系统接口）) | 删除SIM卡消息，msgIndex无效时，删除报错。使用Promise异步回调。 |
| [downloadMms](arkts-telephony-sms-downloadmms-f-sys.md#downloadMms) | 下载彩信。使用callback异步回调。 |
| [downloadMms](arkts-telephony-sms-downloadmms-f-sys.md#downloadMms（系统接口）) | 下载彩信。使用Promise异步回调。 |
| [encodeMms](arkts-telephony-sms-encodemms-f-sys.md#encodeMms) | 彩信编码。使用callback异步回调。 |
| [encodeMms](arkts-telephony-sms-encodemms-f-sys.md#encodeMms（系统接口）) | 彩信编码。使用Promise异步回调。 |
| [getAllSimMessages](arkts-telephony-sms-getallsimmessages-f-sys.md#getAllSimMessages) | 获取所有SIM卡消息。使用callback异步回调。 |
| [getAllSimMessages](arkts-telephony-sms-getallsimmessages-f-sys.md#getAllSimMessages（系统接口）) | 获取所有SIM卡消息。使用Promise异步回调。 |
| [getImsShortMessageFormat](arkts-telephony-sms-getimsshortmessageformat-f-sys.md#getImsShortMessageFormat) | 获取IMS上支持的SMS格式。使用callback异步回调。 |
| [getImsShortMessageFormat](arkts-telephony-sms-getimsshortmessageformat-f-sys.md#getImsShortMessageFormat（系统接口）) | 获取IMS上支持的SMS格式。使用Promise异步回调。 |
| [getSmsSegmentsInfo](arkts-telephony-sms-getsmssegmentsinfo-f-sys.md#getSmsSegmentsInfo) | 获取短信段信息。使用callback异步回调。 |
| [getSmsSegmentsInfo](arkts-telephony-sms-getsmssegmentsinfo-f-sys.md#getSmsSegmentsInfo（系统接口）) | 获取短信段信息。使用Promise异步回调。 |
| [getSmsShortCodeType](arkts-telephony-sms-getsmsshortcodetype-f-sys.md#getSmsShortCodeType) | 获取拟发送短信的目标地址短码类型 |
| [getSmscAddr](arkts-telephony-sms-getsmscaddr-f-sys.md#getSmscAddr) | 获取短信服务中心（SMSC）地址。使用callback异步回调。 |
| [getSmscAddr](arkts-telephony-sms-getsmscaddr-f-sys.md#getSmscAddr（系统接口）) | 获取短信服务中心（SMSC）地址。使用Promise异步回调。 |
| [isImsSmsSupported](arkts-telephony-sms-isimssmssupported-f-sys.md#isImsSmsSupported) | 如果IMS已注册并且在IMS上支持SMS，则支持通过IMS发送SMS。使用callback异步回调。 |
| [isImsSmsSupported](arkts-telephony-sms-isimssmssupported-f-sys.md#isImsSmsSupported（系统接口）) | 如果IMS已注册并且在IMS上支持SMS，则支持通过IMS发送SMS。使用Promise异步回调。 |
| [sendMms](arkts-telephony-sms-sendmms-f-sys.md#sendMms) | 发送彩信。使用callback异步回调。 |
| [sendMms](arkts-telephony-sms-sendmms-f-sys.md#sendMms（系统接口）) | 发送彩信。使用Promise异步回调。 |
| [setCBConfig](arkts-telephony-sms-setcbconfig-f-sys.md#setCBConfig) | 设置小区广播配置。使用callback异步回调。 |
| [setCBConfig](arkts-telephony-sms-setcbconfig-f-sys.md#setCBConfig（系统接口）) | 设置小区广播配置。使用Promise异步回调。 |
| [setCBConfigList](arkts-telephony-sms-setcbconfiglist-f-sys.md#setCBConfigList) | 打开小区广播列表 |
| [setDefaultSmsSlotId](arkts-telephony-sms-setdefaultsmsslotid-f-sys.md#setDefaultSmsSlotId) | 设置发送短信的默认SIM卡槽ID。使用callback异步回调。 |
| [setDefaultSmsSlotId](arkts-telephony-sms-setdefaultsmsslotid-f-sys.md#setDefaultSmsSlotId（系统接口）) | 设置发送短信的默认SIM卡槽ID。使用Promise异步回调。 |
| [setSmscAddr](arkts-telephony-sms-setsmscaddr-f-sys.md#setSmscAddr) | 设置短信服务中心（SMSC）地址。使用callback异步回调。 |
| [setSmscAddr](arkts-telephony-sms-setsmscaddr-f-sys.md#setSmscAddr（系统接口）) | 设置短信服务中心（SMSC）地址。使用Promise异步回调。 |
| [splitMessage](arkts-telephony-sms-splitmessage-f-sys.md#splitMessage) | 将长短信拆分为多个片段。使用callback异步回调。 |
| [splitMessage](arkts-telephony-sms-splitmessage-f-sys.md#splitMessage（系统接口）) | 将长短信拆分为多个片段。使用Promise异步回调。 |
| [updateSimMessage](arkts-telephony-sms-updatesimmessage-f-sys.md#updateSimMessage) | 更新SIM卡消息。使用callback异步回调。 |
| [updateSimMessage](arkts-telephony-sms-updatesimmessage-f-sys.md#updateSimMessage（系统接口）) | 更新SIM卡消息。使用Promise异步回调。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [IDeliveryShortMessageCallback](arkts-telephony-sms-ideliveryshortmessagecallback-i.md) | 回调实例，返回短信送达报告。 |
| [ISendShortMessageCallback](arkts-telephony-sms-isendshortmessagecallback-i.md) | 回调实例。返回短信发送结果、存储已发送短信的URI和是否为长短信的最后一部分。 |
| [SendMessageOptions](arkts-telephony-sms-sendmessageoptions-i.md) | 发送短信的参数和回调。根据SendMessageOptions中的可选参数content的值判断短信类型。 |
| [ShortMessage](arkts-telephony-sms-shortmessage-i.md) | 短信实例。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [CBConfigListConfigs](arkts-telephony-sms-cbconfiglistconfigs-i-sys.md) | 定义小区广播列表配置 |
| [CBConfigOptions](arkts-telephony-sms-cbconfigoptions-i-sys.md) | 小区广播配置选项。 |
| [MmsAcknowledgeInd](arkts-telephony-sms-mmsacknowledgeind-i-sys.md) | 彩信确认索引。 |
| [MmsAddress](arkts-telephony-sms-mmsaddress-i-sys.md) | 彩信地址。 |
| [MmsAttachment](arkts-telephony-sms-mmsattachment-i-sys.md) | 彩信附件。 |
| [MmsConfig](arkts-telephony-sms-mmsconfig-i-sys.md) | 彩信配置文件。 |
| [MmsDeliveryInd](arkts-telephony-sms-mmsdeliveryind-i-sys.md) | 彩信发送标识。 |
| [MmsInformation](arkts-telephony-sms-mmsinformation-i-sys.md) | 彩信信息。 |
| [MmsNotificationInd](arkts-telephony-sms-mmsnotificationind-i-sys.md) | 彩信通知索引。 |
| [MmsParams](arkts-telephony-sms-mmsparams-i-sys.md) | 发送彩信的参数。 |
| [MmsReadOrigInd](arkts-telephony-sms-mmsreadorigind-i-sys.md) | 彩信读取原始索引。 |
| [MmsReadRecInd](arkts-telephony-sms-mmsreadrecind-i-sys.md) | 彩信读取记录索引。 |
| [MmsRespInd](arkts-telephony-sms-mmsrespind-i-sys.md) | 彩信回复标志。 |
| [MmsRetrieveConf](arkts-telephony-sms-mmsretrieveconf-i-sys.md) | 彩信检索配置。 |
| [MmsSendConf](arkts-telephony-sms-mmssendconf-i-sys.md) | 彩信发送配置。 |
| [MmsSendReq](arkts-telephony-sms-mmssendreq-i-sys.md) | 彩信发送请求。 |
| [SimMessageOptions](arkts-telephony-sms-simmessageoptions-i-sys.md) | SIM卡消息选项。 |
| [SimShortMessage](arkts-telephony-sms-simshortmessage-i-sys.md) | SIM卡短消息。 |
| [SmsSegmentsInfo](arkts-telephony-sms-smssegmentsinfo-i-sys.md) | 短信段信息。 |
| [UpdateSimMessageOptions](arkts-telephony-sms-updatesimmessageoptions-i-sys.md) | 更新SIM卡消息选项。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [SendSmsResult](arkts-telephony-sms-sendsmsresult-e.md) | 短信发送结果。 |
| [ShortMessageClass](arkts-telephony-sms-shortmessageclass-e.md) | 短信类型。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DispositionType](arkts-telephony-sms-dispositiontype-e-sys.md) | 处理类型。 |
| [MessageType](arkts-telephony-sms-messagetype-e-sys.md) | 消息类型。 |
| [MmsCharSets](arkts-telephony-sms-mmscharsets-e-sys.md) | 彩信字符集。 |
| [MmsPriorityType](arkts-telephony-sms-mmsprioritytype-e-sys.md) | 彩信优先级类型。 |
| [MmsVersionType](arkts-telephony-sms-mmsversiontype-e-sys.md) | 彩信版本类型。 |
| [RanType](arkts-telephony-sms-rantype-e-sys.md) | 设备网络制式。 |
| [ReportType](arkts-telephony-sms-reporttype-e-sys.md) | 报告类型。 |
| [SimMessageStatus](arkts-telephony-sms-simmessagestatus-e-sys.md) | SIM卡消息状态。 |
| [SmsEncodingScheme](arkts-telephony-sms-smsencodingscheme-e-sys.md) | 短信编码方案。 |
| [SmsShortCodeType](arkts-telephony-sms-smsshortcodetype-e-sys.md) | 短信短码类型 |
<!--DelEnd-->

