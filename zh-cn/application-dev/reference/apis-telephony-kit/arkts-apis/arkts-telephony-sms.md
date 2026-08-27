# @ohos.telephony.sms(短信服务)

短信服务提供了管理短信的一些基础能力，包括创建、发送短信，获取发送短信的默认SIM卡槽ID、检查当前设备是否具备短信发送和接收能力等。

**起始版本：** 6

**系统能力：** SystemCapability.Telephony.SmsMms

## 导入模块

```TypeScript
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createMessage(短信服务)](arkts-telephony-sms-createmessage-f.md) | 根据协议数据单元(PDU)和指定的短信协议创建短信实例。使用callback异步回调。 |
| [createMessage(短信服务)](arkts-telephony-sms-createmessage-f.md) | 根据协议数据单元(PDU)和指定的短信协议创建短信实例。使用Promise异步回调。 |
| [getDefaultSmsSimId(短信服务)](arkts-telephony-sms-getdefaultsmssimid-f.md) | 获取发送短信的默认SIM卡ID。使用callback异步回调。 |
| [getDefaultSmsSimId(短信服务)](arkts-telephony-sms-getdefaultsmssimid-f.md) | 获取发送短信的默认SIM卡ID。使用Promise异步回调。 |
| [getDefaultSmsSlotId(短信服务)](arkts-telephony-sms-getdefaultsmsslotid-f.md) | 获取发送短信的默认SIM卡槽ID。使用callback异步回调。 |
| [getDefaultSmsSlotId(短信服务)](arkts-telephony-sms-getdefaultsmsslotid-f.md) | 获取发送短信的默认SIM卡槽ID。使用Promise异步回调。 |
| [hasSmsCapability(短信服务)](arkts-telephony-sms-hassmscapability-f.md) | 检查当前设备是否具备短信发送和接收能力，该方法是同步方法。 |
| [sendMessage(短信服务)](arkts-telephony-sms-sendmessage-f.md) | 发送短信。 |
| [sendShortMessage(短信服务)](arkts-telephony-sms-sendshortmessage-f.md) | 发送短信。使用callback异步回调。 |
| [sendShortMessage(短信服务)](arkts-telephony-sms-sendshortmessage-f.md) | 发送短信。使用Promise异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [addSimMessage(短信服务)](arkts-telephony-sms-addsimmessage-f-sys.md) | 添加SIM卡消息，sim卡消息满，添加报错。使用callback异步回调。 |
| [addSimMessage(短信服务)](arkts-telephony-sms-addsimmessage-f-sys.md) | 添加SIM卡消息，sim卡消息满，添加报错。使用Promise异步回调。 |
| [decodeMms(短信服务)](arkts-telephony-sms-decodemms-f-sys.md) | 彩信解码。使用callback异步回调。 |
| [decodeMms(短信服务)](arkts-telephony-sms-decodemms-f-sys.md) | 彩信解码。使用Promise异步回调。 |
| [delSimMessage(短信服务)](arkts-telephony-sms-delsimmessage-f-sys.md) | 删除SIM卡消息，msgIndex无效时，删除报错。使用callback异步回调。 |
| [delSimMessage(短信服务)](arkts-telephony-sms-delsimmessage-f-sys.md) | 删除SIM卡消息，msgIndex无效时，删除报错。使用Promise异步回调。 |
| [downloadMms(短信服务)](arkts-telephony-sms-downloadmms-f-sys.md) | 下载彩信。使用callback异步回调。 |
| [downloadMms(短信服务)](arkts-telephony-sms-downloadmms-f-sys.md) | 下载彩信。使用Promise异步回调。 |
| [encodeMms(短信服务)](arkts-telephony-sms-encodemms-f-sys.md) | 彩信编码。使用callback异步回调。 |
| [encodeMms(短信服务)](arkts-telephony-sms-encodemms-f-sys.md) | 彩信编码。使用Promise异步回调。 |
| [getAllSimMessages(短信服务)](arkts-telephony-sms-getallsimmessages-f-sys.md) | 获取所有SIM卡消息。使用callback异步回调。 |
| [getAllSimMessages(短信服务)](arkts-telephony-sms-getallsimmessages-f-sys.md) | 获取所有SIM卡消息。使用Promise异步回调。 |
| [getImsShortMessageFormat(短信服务)](arkts-telephony-sms-getimsshortmessageformat-f-sys.md) | 获取IMS上支持的SMS格式。使用callback异步回调。 |
| [getImsShortMessageFormat(短信服务)](arkts-telephony-sms-getimsshortmessageformat-f-sys.md) | 获取IMS上支持的SMS格式。使用Promise异步回调。 |
| [getSmscAddr(短信服务)](arkts-telephony-sms-getsmscaddr-f-sys.md) | 获取短信服务中心（SMSC）地址。使用callback异步回调。 |
| [getSmscAddr(短信服务)](arkts-telephony-sms-getsmscaddr-f-sys.md) | 获取短信服务中心（SMSC）地址。使用Promise异步回调。 |
| [getSmsSegmentsInfo(短信服务)](arkts-telephony-sms-getsmssegmentsinfo-f-sys.md) | 获取短信段信息。使用callback异步回调。 |
| [getSmsSegmentsInfo(短信服务)](arkts-telephony-sms-getsmssegmentsinfo-f-sys.md) | 获取短信段信息。使用Promise异步回调。 |
| [getSmsShortCodeType(短信服务)](arkts-telephony-sms-getsmsshortcodetype-f-sys.md) | 获取拟发送短信的目标地址短码类型 |
| [isImsSmsSupported(短信服务)](arkts-telephony-sms-isimssmssupported-f-sys.md) | 如果IMS已注册并且在IMS上支持SMS，则支持通过IMS发送SMS。使用callback异步回调。 |
| [isImsSmsSupported(短信服务)](arkts-telephony-sms-isimssmssupported-f-sys.md) | 如果IMS已注册并且在IMS上支持SMS，则支持通过IMS发送SMS。使用Promise异步回调。 |
| [sendMms(短信服务)](arkts-telephony-sms-sendmms-f-sys.md) | 发送彩信。使用callback异步回调。 |
| [sendMms(短信服务)](arkts-telephony-sms-sendmms-f-sys.md) | 发送彩信。使用Promise异步回调。 |
| [setCBConfig(短信服务)](arkts-telephony-sms-setcbconfig-f-sys.md) | 设置小区广播配置。使用callback异步回调。 |
| [setCBConfig(短信服务)](arkts-telephony-sms-setcbconfig-f-sys.md) | 设置小区广播配置。使用Promise异步回调。 |
| [setCBConfigList(短信服务)](arkts-telephony-sms-setcbconfiglist-f-sys.md) | 打开小区广播列表 |
| [setDefaultSmsSlotId(短信服务)](arkts-telephony-sms-setdefaultsmsslotid-f-sys.md) | 设置发送短信的默认SIM卡槽ID。使用callback异步回调。 |
| [setDefaultSmsSlotId(短信服务)](arkts-telephony-sms-setdefaultsmsslotid-f-sys.md) | 设置发送短信的默认SIM卡槽ID。使用Promise异步回调。 |
| [setSmscAddr(短信服务)](arkts-telephony-sms-setsmscaddr-f-sys.md) | 设置短信服务中心（SMSC）地址。使用callback异步回调。 |
| [setSmscAddr(短信服务)](arkts-telephony-sms-setsmscaddr-f-sys.md) | 设置短信服务中心（SMSC）地址。使用Promise异步回调。 |
| [splitMessage(短信服务)](arkts-telephony-sms-splitmessage-f-sys.md) | 将长短信拆分为多个片段。使用callback异步回调。 |
| [splitMessage(短信服务)](arkts-telephony-sms-splitmessage-f-sys.md) | 将长短信拆分为多个片段。使用Promise异步回调。 |
| [updateSimMessage(短信服务)](arkts-telephony-sms-updatesimmessage-f-sys.md) | 更新SIM卡消息。使用callback异步回调。 |
| [updateSimMessage(短信服务)](arkts-telephony-sms-updatesimmessage-f-sys.md) | 更新SIM卡消息。使用Promise异步回调。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [IDeliveryShortMessageCallback(短信服务)](arkts-telephony-sms-ideliveryshortmessagecallback-i.md) | 回调实例，返回短信送达报告。 |
| [ISendShortMessageCallback(短信服务)](arkts-telephony-sms-isendshortmessagecallback-i.md) | 回调实例。返回短信发送结果、存储已发送短信的URI和是否为长短信的最后一部分。 |
| [SendMessageOptions(短信服务)](arkts-telephony-sms-sendmessageoptions-i.md) | 发送短信的参数和回调。根据SendMessageOptions中的可选参数content的值判断短信类型。 |
| [ShortMessage(短信服务)](arkts-telephony-sms-shortmessage-i.md) | 短信实例。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [CBConfigListConfigs(短信服务)](arkts-telephony-sms-cbconfiglistconfigs-i-sys.md) | 定义小区广播列表配置 |
| [CBConfigOptions(短信服务)](arkts-telephony-sms-cbconfigoptions-i-sys.md) | 小区广播配置选项。 |
| [MmsAcknowledgeInd(短信服务)](arkts-telephony-sms-mmsacknowledgeind-i-sys.md) | 彩信确认索引。 |
| [MmsAddress(短信服务)](arkts-telephony-sms-mmsaddress-i-sys.md) | 彩信地址。 |
| [MmsAttachment(短信服务)](arkts-telephony-sms-mmsattachment-i-sys.md) | 彩信附件。 |
| [MmsConfig(短信服务)](arkts-telephony-sms-mmsconfig-i-sys.md) | 彩信配置文件。 |
| [MmsDeliveryInd(短信服务)](arkts-telephony-sms-mmsdeliveryind-i-sys.md) | 彩信发送标识。 |
| [MmsInformation(短信服务)](arkts-telephony-sms-mmsinformation-i-sys.md) | 彩信信息。 |
| [MmsNotificationInd(短信服务)](arkts-telephony-sms-mmsnotificationind-i-sys.md) | 彩信通知索引。 |
| [MmsParams(短信服务)](arkts-telephony-sms-mmsparams-i-sys.md) | 发送彩信的参数。 |
| [MmsReadOrigInd(短信服务)](arkts-telephony-sms-mmsreadorigind-i-sys.md) | 彩信读取原始索引。 |
| [MmsReadRecInd(短信服务)](arkts-telephony-sms-mmsreadrecind-i-sys.md) | 彩信读取记录索引。 |
| [MmsRespInd(短信服务)](arkts-telephony-sms-mmsrespind-i-sys.md) | 彩信回复标志。 |
| [MmsRetrieveConf(短信服务)](arkts-telephony-sms-mmsretrieveconf-i-sys.md) | 彩信检索配置。 |
| [MmsSendConf(短信服务)](arkts-telephony-sms-mmssendconf-i-sys.md) | 彩信发送配置。 |
| [MmsSendReq(短信服务)](arkts-telephony-sms-mmssendreq-i-sys.md) | 彩信发送请求。 |
| [SimMessageOptions(短信服务)](arkts-telephony-sms-simmessageoptions-i-sys.md) | SIM卡消息选项。 |
| [SimShortMessage(短信服务)](arkts-telephony-sms-simshortmessage-i-sys.md) | SIM卡短消息。 |
| [SmsSegmentsInfo(短信服务)](arkts-telephony-sms-smssegmentsinfo-i-sys.md) | 短信段信息。 |
| [UpdateSimMessageOptions(短信服务)](arkts-telephony-sms-updatesimmessageoptions-i-sys.md) | 更新SIM卡消息选项。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [SendSmsResult(短信服务)](arkts-telephony-sms-sendsmsresult-e.md) | 短信发送结果。 |
| [ShortMessageClass(短信服务)](arkts-telephony-sms-shortmessageclass-e.md) | 短信类型。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DispositionType(短信服务)](arkts-telephony-sms-dispositiontype-e-sys.md) | 处理类型。 |
| [MessageType(短信服务)](arkts-telephony-sms-messagetype-e-sys.md) | 消息类型。 |
| [MmsCharSets(短信服务)](arkts-telephony-sms-mmscharsets-e-sys.md) | 彩信字符集。 |
| [MmsPriorityType(短信服务)](arkts-telephony-sms-mmsprioritytype-e-sys.md) | 彩信优先级类型。 |
| [MmsVersionType(短信服务)](arkts-telephony-sms-mmsversiontype-e-sys.md) | 彩信版本类型。 |
| [RanType(短信服务)](arkts-telephony-sms-rantype-e-sys.md) | 设备网络制式。 |
| [ReportType(短信服务)](arkts-telephony-sms-reporttype-e-sys.md) | 报告类型。 |
| [SimMessageStatus(短信服务)](arkts-telephony-sms-simmessagestatus-e-sys.md) | SIM卡消息状态。 |
| [SmsEncodingScheme(短信服务)](arkts-telephony-sms-smsencodingscheme-e-sys.md) | 短信编码方案。 |
| [SmsShortCodeType(短信服务)](arkts-telephony-sms-smsshortcodetype-e-sys.md) | 短信短码类型 |
<!--DelEnd-->
