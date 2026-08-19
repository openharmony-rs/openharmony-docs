# DisconnectedReason（系统接口）

断开连接的详细信息。

**起始版本：** 23

<!--Device-call-export enum DisconnectedReason--><!--Device-call-export enum DisconnectedReason-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## UNASSIGNED_NUMBER

```TypeScript
UNASSIGNED_NUMBER = 1
```

未分配的号码(空号)。

**起始版本：** 23

<!--Device-DisconnectedReason-UNASSIGNED_NUMBER = 1--><!--Device-DisconnectedReason-UNASSIGNED_NUMBER = 1-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## NO_ROUTE_TO_DESTINATION

```TypeScript
NO_ROUTE_TO_DESTINATION = 3
```

无至目的地的路由。

**起始版本：** 23

<!--Device-DisconnectedReason-NO_ROUTE_TO_DESTINATION = 3--><!--Device-DisconnectedReason-NO_ROUTE_TO_DESTINATION = 3-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## CHANNEL_UNACCEPTABLE

```TypeScript
CHANNEL_UNACCEPTABLE = 6
```

不可接受的通路。

**起始版本：** 23

<!--Device-DisconnectedReason-CHANNEL_UNACCEPTABLE = 6--><!--Device-DisconnectedReason-CHANNEL_UNACCEPTABLE = 6-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## OPERATOR_DETERMINED_BARRING

```TypeScript
OPERATOR_DETERMINED_BARRING = 8
```

运营商闭锁。

**起始版本：** 23

<!--Device-DisconnectedReason-OPERATOR_DETERMINED_BARRING = 8--><!--Device-DisconnectedReason-OPERATOR_DETERMINED_BARRING = 8-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## CALL_COMPLETED_ELSEWHERE

```TypeScript
CALL_COMPLETED_ELSEWHERE = 13
```

呼叫在其他地方完成。

**起始版本：** 23

<!--Device-DisconnectedReason-CALL_COMPLETED_ELSEWHERE = 13--><!--Device-DisconnectedReason-CALL_COMPLETED_ELSEWHERE = 13-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## NORMAL_CALL_CLEARING

```TypeScript
NORMAL_CALL_CLEARING = 16
```

清除正常呼叫。

**起始版本：** 23

<!--Device-DisconnectedReason-NORMAL_CALL_CLEARING = 16--><!--Device-DisconnectedReason-NORMAL_CALL_CLEARING = 16-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## USER_BUSY

```TypeScript
USER_BUSY = 17
```

用户忙。

**起始版本：** 23

<!--Device-DisconnectedReason-USER_BUSY = 17--><!--Device-DisconnectedReason-USER_BUSY = 17-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## NO_USER_RESPONDING

```TypeScript
NO_USER_RESPONDING = 18
```

无用户响应。

**起始版本：** 23

<!--Device-DisconnectedReason-NO_USER_RESPONDING = 18--><!--Device-DisconnectedReason-NO_USER_RESPONDING = 18-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## USER_ALERTING_NO_ANSWER

```TypeScript
USER_ALERTING_NO_ANSWER = 19
```

已有用户提醒，但无应答。

**起始版本：** 23

<!--Device-DisconnectedReason-USER_ALERTING_NO_ANSWER = 19--><!--Device-DisconnectedReason-USER_ALERTING_NO_ANSWER = 19-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## CALL_REJECTED

```TypeScript
CALL_REJECTED = 21
```

呼叫拒绝。

**起始版本：** 23

<!--Device-DisconnectedReason-CALL_REJECTED = 21--><!--Device-DisconnectedReason-CALL_REJECTED = 21-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## NUMBER_CHANGED

```TypeScript
NUMBER_CHANGED = 22
```

号码改变。

**起始版本：** 23

<!--Device-DisconnectedReason-NUMBER_CHANGED = 22--><!--Device-DisconnectedReason-NUMBER_CHANGED = 22-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## CALL_REJECTED_DUE_TO_FEATURE_AT_THE_DESTINATION

```TypeScript
CALL_REJECTED_DUE_TO_FEATURE_AT_THE_DESTINATION = 24
```

当由于目标地址(例如匿名)导致呼叫被拒绝。

**起始版本：** 23

<!--Device-DisconnectedReason-CALL_REJECTED_DUE_TO_FEATURE_AT_THE_DESTINATION = 24--><!--Device-DisconnectedReason-CALL_REJECTED_DUE_TO_FEATURE_AT_THE_DESTINATION = 24-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## FAILED_PRE_EMPTION

```TypeScript
FAILED_PRE_EMPTION = 25
```

抢占失败。

**起始版本：** 23

<!--Device-DisconnectedReason-FAILED_PRE_EMPTION = 25--><!--Device-DisconnectedReason-FAILED_PRE_EMPTION = 25-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## NON_SELECTED_USER_CLEARING

```TypeScript
NON_SELECTED_USER_CLEARING = 26
```

非选定用户清除。

**起始版本：** 23

<!--Device-DisconnectedReason-NON_SELECTED_USER_CLEARING = 26--><!--Device-DisconnectedReason-NON_SELECTED_USER_CLEARING = 26-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## DESTINATION_OUT_OF_ORDER

```TypeScript
DESTINATION_OUT_OF_ORDER = 27
```

终点故障。

**起始版本：** 23

<!--Device-DisconnectedReason-DESTINATION_OUT_OF_ORDER = 27--><!--Device-DisconnectedReason-DESTINATION_OUT_OF_ORDER = 27-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## INVALID_NUMBER_FORMAT

```TypeScript
INVALID_NUMBER_FORMAT = 28
```

无效号码格式。

**起始版本：** 23

<!--Device-DisconnectedReason-INVALID_NUMBER_FORMAT = 28--><!--Device-DisconnectedReason-INVALID_NUMBER_FORMAT = 28-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## FACILITY_REJECTED

```TypeScript
FACILITY_REJECTED = 29
```

增补业务拒绝。

**起始版本：** 23

<!--Device-DisconnectedReason-FACILITY_REJECTED = 29--><!--Device-DisconnectedReason-FACILITY_REJECTED = 29-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## RESPONSE_TO_STATUS_ENQUIRY

```TypeScript
RESPONSE_TO_STATUS_ENQUIRY = 30
```

对状态查询的响应。

**起始版本：** 23

<!--Device-DisconnectedReason-RESPONSE_TO_STATUS_ENQUIRY = 30--><!--Device-DisconnectedReason-RESPONSE_TO_STATUS_ENQUIRY = 30-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## NORMAL_UNSPECIFIED

```TypeScript
NORMAL_UNSPECIFIED = 31
```

正常，未指定。

**起始版本：** 23

<!--Device-DisconnectedReason-NORMAL_UNSPECIFIED = 31--><!--Device-DisconnectedReason-NORMAL_UNSPECIFIED = 31-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## NO_CIRCUIT_CHANNEL_AVAILABLE

```TypeScript
NO_CIRCUIT_CHANNEL_AVAILABLE = 34
```

无电路/通道可用。

**起始版本：** 23

<!--Device-DisconnectedReason-NO_CIRCUIT_CHANNEL_AVAILABLE = 34--><!--Device-DisconnectedReason-NO_CIRCUIT_CHANNEL_AVAILABLE = 34-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## NETWORK_OUT_OF_ORDER

```TypeScript
NETWORK_OUT_OF_ORDER = 38
```

网络故障。

**起始版本：** 23

<!--Device-DisconnectedReason-NETWORK_OUT_OF_ORDER = 38--><!--Device-DisconnectedReason-NETWORK_OUT_OF_ORDER = 38-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## TEMPORARY_FAILURE

```TypeScript
TEMPORARY_FAILURE = 41
```

临时故障。

**起始版本：** 23

<!--Device-DisconnectedReason-TEMPORARY_FAILURE = 41--><!--Device-DisconnectedReason-TEMPORARY_FAILURE = 41-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## SWITCHING_EQUIPMENT_CONGESTION

```TypeScript
SWITCHING_EQUIPMENT_CONGESTION = 42
```

交换设备拥塞。

**起始版本：** 23

<!--Device-DisconnectedReason-SWITCHING_EQUIPMENT_CONGESTION = 42--><!--Device-DisconnectedReason-SWITCHING_EQUIPMENT_CONGESTION = 42-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## ACCESS_INFORMATION_DISCARDED

```TypeScript
ACCESS_INFORMATION_DISCARDED = 43
```

已丢弃访问信息。

**起始版本：** 23

<!--Device-DisconnectedReason-ACCESS_INFORMATION_DISCARDED = 43--><!--Device-DisconnectedReason-ACCESS_INFORMATION_DISCARDED = 43-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## REQUEST_CIRCUIT_CHANNEL_NOT_AVAILABLE

```TypeScript
REQUEST_CIRCUIT_CHANNEL_NOT_AVAILABLE = 44
```

请求的电路/通道不可用。

**起始版本：** 23

<!--Device-DisconnectedReason-REQUEST_CIRCUIT_CHANNEL_NOT_AVAILABLE = 44--><!--Device-DisconnectedReason-REQUEST_CIRCUIT_CHANNEL_NOT_AVAILABLE = 44-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## RESOURCES_UNAVAILABLE_UNSPECIFIED

```TypeScript
RESOURCES_UNAVAILABLE_UNSPECIFIED = 47
```

未指定资源不可用。

**起始版本：** 23

<!--Device-DisconnectedReason-RESOURCES_UNAVAILABLE_UNSPECIFIED = 47--><!--Device-DisconnectedReason-RESOURCES_UNAVAILABLE_UNSPECIFIED = 47-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## QUALITY_OF_SERVICE_UNAVAILABLE

```TypeScript
QUALITY_OF_SERVICE_UNAVAILABLE = 49
```

服务质量不可用。

**起始版本：** 23

<!--Device-DisconnectedReason-QUALITY_OF_SERVICE_UNAVAILABLE = 49--><!--Device-DisconnectedReason-QUALITY_OF_SERVICE_UNAVAILABLE = 49-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## REQUESTED_FACILITY_NOT_SUBSCRIBED

```TypeScript
REQUESTED_FACILITY_NOT_SUBSCRIBED = 50
```

请求的设施未订阅。

**起始版本：** 23

<!--Device-DisconnectedReason-REQUESTED_FACILITY_NOT_SUBSCRIBED = 50--><!--Device-DisconnectedReason-REQUESTED_FACILITY_NOT_SUBSCRIBED = 50-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## INCOMING_CALLS_BARRED_WITHIN_THE_CUG

```TypeScript
INCOMING_CALLS_BARRED_WITHIN_THE_CUG = 55
```

CUG内禁止来电。

**起始版本：** 23

<!--Device-DisconnectedReason-INCOMING_CALLS_BARRED_WITHIN_THE_CUG = 55--><!--Device-DisconnectedReason-INCOMING_CALLS_BARRED_WITHIN_THE_CUG = 55-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## BEARER_CAPABILITY_NOT_AUTHORIZED

```TypeScript
BEARER_CAPABILITY_NOT_AUTHORIZED = 57
```

未授权承载能力。

**起始版本：** 23

<!--Device-DisconnectedReason-BEARER_CAPABILITY_NOT_AUTHORIZED = 57--><!--Device-DisconnectedReason-BEARER_CAPABILITY_NOT_AUTHORIZED = 57-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## BEARER_CAPABILITY_NOT_PRESENTLY_AVAILABLE

```TypeScript
BEARER_CAPABILITY_NOT_PRESENTLY_AVAILABLE = 58
```

承载能力目前不可用。

**起始版本：** 23

<!--Device-DisconnectedReason-BEARER_CAPABILITY_NOT_PRESENTLY_AVAILABLE = 58--><!--Device-DisconnectedReason-BEARER_CAPABILITY_NOT_PRESENTLY_AVAILABLE = 58-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## SERVICE_OR_OPTION_NOT_AVAILABLE_UNSPECIFIED

```TypeScript
SERVICE_OR_OPTION_NOT_AVAILABLE_UNSPECIFIED = 63
```

服务或选项不可用，未指定。

**起始版本：** 23

<!--Device-DisconnectedReason-SERVICE_OR_OPTION_NOT_AVAILABLE_UNSPECIFIED = 63--><!--Device-DisconnectedReason-SERVICE_OR_OPTION_NOT_AVAILABLE_UNSPECIFIED = 63-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## BEARER_SERVICE_NOT_IMPLEMENTED

```TypeScript
BEARER_SERVICE_NOT_IMPLEMENTED = 65
```

未实现承载服务。

**起始版本：** 23

<!--Device-DisconnectedReason-BEARER_SERVICE_NOT_IMPLEMENTED = 65--><!--Device-DisconnectedReason-BEARER_SERVICE_NOT_IMPLEMENTED = 65-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## ACM_EQUALTO_OR_GREATER_THAN_THE_MAXIMUM_VALUE

```TypeScript
ACM_EQUALTO_OR_GREATER_THAN_THE_MAXIMUM_VALUE = 68
```

ACM大于或等于最大值。

**起始版本：** 23

<!--Device-DisconnectedReason-ACM_EQUALTO_OR_GREATER_THAN_THE_MAXIMUM_VALUE = 68--><!--Device-DisconnectedReason-ACM_EQUALTO_OR_GREATER_THAN_THE_MAXIMUM_VALUE = 68-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## REQUESTED_FACILITY_NOT_IMPLEMENTED

```TypeScript
REQUESTED_FACILITY_NOT_IMPLEMENTED = 69
```

请求的设施未实施。

**起始版本：** 23

<!--Device-DisconnectedReason-REQUESTED_FACILITY_NOT_IMPLEMENTED = 69--><!--Device-DisconnectedReason-REQUESTED_FACILITY_NOT_IMPLEMENTED = 69-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## ONLY_RESTRICTED_DIGITAL_INFO_BEARER_CAPABILITY_IS_AVAILABLE

```TypeScript
ONLY_RESTRICTED_DIGITAL_INFO_BEARER_CAPABILITY_IS_AVAILABLE = 70
```

仅限BC有限数字信息可用。

**起始版本：** 23

<!--Device-DisconnectedReason-ONLY_RESTRICTED_DIGITAL_INFO_BEARER_CAPABILITY_IS_AVAILABLE = 70--><!--Device-DisconnectedReason-ONLY_RESTRICTED_DIGITAL_INFO_BEARER_CAPABILITY_IS_AVAILABLE = 70-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## SERVICE_OR_OPTION_NOT_IMPLEMENTED_UNSPECIFIED

```TypeScript
SERVICE_OR_OPTION_NOT_IMPLEMENTED_UNSPECIFIED = 79
```

服务或选项未实施，未指定。

**起始版本：** 23

<!--Device-DisconnectedReason-SERVICE_OR_OPTION_NOT_IMPLEMENTED_UNSPECIFIED = 79--><!--Device-DisconnectedReason-SERVICE_OR_OPTION_NOT_IMPLEMENTED_UNSPECIFIED = 79-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## INVALID_TRANSACTION_IDENTIFIER_VALUE

```TypeScript
INVALID_TRANSACTION_IDENTIFIER_VALUE = 81
```

无效的业务标识符值。

**起始版本：** 23

<!--Device-DisconnectedReason-INVALID_TRANSACTION_IDENTIFIER_VALUE = 81--><!--Device-DisconnectedReason-INVALID_TRANSACTION_IDENTIFIER_VALUE = 81-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## USER_NOT_MEMBER_OF_CUG

```TypeScript
USER_NOT_MEMBER_OF_CUG = 87
```

用户不是CUG成员。

**起始版本：** 23

<!--Device-DisconnectedReason-USER_NOT_MEMBER_OF_CUG = 87--><!--Device-DisconnectedReason-USER_NOT_MEMBER_OF_CUG = 87-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## INCOMPATIBLE_DESTINATION

```TypeScript
INCOMPATIBLE_DESTINATION = 88
```

目标不兼容。

**起始版本：** 23

<!--Device-DisconnectedReason-INCOMPATIBLE_DESTINATION = 88--><!--Device-DisconnectedReason-INCOMPATIBLE_DESTINATION = 88-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## INVALID_TRANSIT_NETWORK_SELECTION

```TypeScript
INVALID_TRANSIT_NETWORK_SELECTION = 91
```

选择的传输网络无效。

**起始版本：** 23

<!--Device-DisconnectedReason-INVALID_TRANSIT_NETWORK_SELECTION = 91--><!--Device-DisconnectedReason-INVALID_TRANSIT_NETWORK_SELECTION = 91-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## SEMANTICALLY_INCORRECT_MESSAGE

```TypeScript
SEMANTICALLY_INCORRECT_MESSAGE = 95
```

语义错误的消息。

**起始版本：** 23

<!--Device-DisconnectedReason-SEMANTICALLY_INCORRECT_MESSAGE = 95--><!--Device-DisconnectedReason-SEMANTICALLY_INCORRECT_MESSAGE = 95-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## INVALID_MANDATORY_INFORMATION

```TypeScript
INVALID_MANDATORY_INFORMATION = 96
```

无效的强制信息。

**起始版本：** 23

<!--Device-DisconnectedReason-INVALID_MANDATORY_INFORMATION = 96--><!--Device-DisconnectedReason-INVALID_MANDATORY_INFORMATION = 96-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## MESSAGE_TYPE_NON_EXISTENT_OR_NOT_IMPLEMENTED

```TypeScript
MESSAGE_TYPE_NON_EXISTENT_OR_NOT_IMPLEMENTED = 97
```

消息类型不存在或未实现。

**起始版本：** 23

<!--Device-DisconnectedReason-MESSAGE_TYPE_NON_EXISTENT_OR_NOT_IMPLEMENTED = 97--><!--Device-DisconnectedReason-MESSAGE_TYPE_NON_EXISTENT_OR_NOT_IMPLEMENTED = 97-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## MESSAGE_TYPE_NOT_COMPATIBLE_WITH_PROTOCOL_STATE

```TypeScript
MESSAGE_TYPE_NOT_COMPATIBLE_WITH_PROTOCOL_STATE = 98
```

消息类型与协议状态不兼容。

**起始版本：** 23

<!--Device-DisconnectedReason-MESSAGE_TYPE_NOT_COMPATIBLE_WITH_PROTOCOL_STATE = 98--><!--Device-DisconnectedReason-MESSAGE_TYPE_NOT_COMPATIBLE_WITH_PROTOCOL_STATE = 98-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## INFORMATION_ELEMENT_NON_EXISTENT_OR_NOT_IMPLEMENTED

```TypeScript
INFORMATION_ELEMENT_NON_EXISTENT_OR_NOT_IMPLEMENTED = 99
```

IE不存在或未实现。

**起始版本：** 23

<!--Device-DisconnectedReason-INFORMATION_ELEMENT_NON_EXISTENT_OR_NOT_IMPLEMENTED = 99--><!--Device-DisconnectedReason-INFORMATION_ELEMENT_NON_EXISTENT_OR_NOT_IMPLEMENTED = 99-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## CONDITIONAL_IE_ERROR

```TypeScript
CONDITIONAL_IE_ERROR = 100
```

条件IE错误。

**起始版本：** 23

<!--Device-DisconnectedReason-CONDITIONAL_IE_ERROR = 100--><!--Device-DisconnectedReason-CONDITIONAL_IE_ERROR = 100-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## MESSAGE_NOT_COMPATIBLE_WITH_PROTOCOL_STATE

```TypeScript
MESSAGE_NOT_COMPATIBLE_WITH_PROTOCOL_STATE = 101
```

消息与协议状态不兼容。

**起始版本：** 23

<!--Device-DisconnectedReason-MESSAGE_NOT_COMPATIBLE_WITH_PROTOCOL_STATE = 101--><!--Device-DisconnectedReason-MESSAGE_NOT_COMPATIBLE_WITH_PROTOCOL_STATE = 101-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## RECOVERY_ON_TIMER_EXPIRED

```TypeScript
RECOVERY_ON_TIMER_EXPIRED = 102
```

计时器过期时恢复计时器编号。

**起始版本：** 23

<!--Device-DisconnectedReason-RECOVERY_ON_TIMER_EXPIRED = 102--><!--Device-DisconnectedReason-RECOVERY_ON_TIMER_EXPIRED = 102-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## PROTOCOL_ERROR_UNSPECIFIED

```TypeScript
PROTOCOL_ERROR_UNSPECIFIED = 111
```

协议错误，未指定。

**起始版本：** 23

<!--Device-DisconnectedReason-PROTOCOL_ERROR_UNSPECIFIED = 111--><!--Device-DisconnectedReason-PROTOCOL_ERROR_UNSPECIFIED = 111-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## INTERWORKING_UNSPECIFIED

```TypeScript
INTERWORKING_UNSPECIFIED = 127
```

互通，未指定。

**起始版本：** 23

<!--Device-DisconnectedReason-INTERWORKING_UNSPECIFIED = 127--><!--Device-DisconnectedReason-INTERWORKING_UNSPECIFIED = 127-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## CALL_BARRED

```TypeScript
CALL_BARRED = 240
```

呼叫被禁止。

**起始版本：** 23

<!--Device-DisconnectedReason-CALL_BARRED = 240--><!--Device-DisconnectedReason-CALL_BARRED = 240-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## FDN_BLOCKED

```TypeScript
FDN_BLOCKED = 241
```

FDN受阻。

**起始版本：** 23

<!--Device-DisconnectedReason-FDN_BLOCKED = 241--><!--Device-DisconnectedReason-FDN_BLOCKED = 241-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## IMSI_UNKNOWN_IN_VLR

```TypeScript
IMSI_UNKNOWN_IN_VLR = 242
```

VLR中的IMSI未知。

**起始版本：** 23

<!--Device-DisconnectedReason-IMSI_UNKNOWN_IN_VLR = 242--><!--Device-DisconnectedReason-IMSI_UNKNOWN_IN_VLR = 242-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## IMEI_NOT_ACCEPTED

```TypeScript
IMEI_NOT_ACCEPTED = 243
```

IMEI未被接受。

**起始版本：** 23

<!--Device-DisconnectedReason-IMEI_NOT_ACCEPTED = 243--><!--Device-DisconnectedReason-IMEI_NOT_ACCEPTED = 243-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## DIAL_MODIFIED_TO_USSD

```TypeScript
DIAL_MODIFIED_TO_USSD = 244
```

拨号修改为USSD。

**起始版本：** 23

<!--Device-DisconnectedReason-DIAL_MODIFIED_TO_USSD = 244--><!--Device-DisconnectedReason-DIAL_MODIFIED_TO_USSD = 244-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## DIAL_MODIFIED_TO_SS

```TypeScript
DIAL_MODIFIED_TO_SS = 245
```

拨号修改为USSD号。

**起始版本：** 23

<!--Device-DisconnectedReason-DIAL_MODIFIED_TO_SS = 245--><!--Device-DisconnectedReason-DIAL_MODIFIED_TO_SS = 245-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## DIAL_MODIFIED_TO_DIAL

```TypeScript
DIAL_MODIFIED_TO_DIAL = 246
```

拨号已修改为正常。

**起始版本：** 23

<!--Device-DisconnectedReason-DIAL_MODIFIED_TO_DIAL = 246--><!--Device-DisconnectedReason-DIAL_MODIFIED_TO_DIAL = 246-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## RADIO_OFF

```TypeScript
RADIO_OFF = 247
```

无线电通讯已关闭。

**起始版本：** 23

<!--Device-DisconnectedReason-RADIO_OFF = 247--><!--Device-DisconnectedReason-RADIO_OFF = 247-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## OUT_OF_SERVICE

```TypeScript
OUT_OF_SERVICE = 248
```

停止服务。

**起始版本：** 23

<!--Device-DisconnectedReason-OUT_OF_SERVICE = 248--><!--Device-DisconnectedReason-OUT_OF_SERVICE = 248-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## NO_VALID_SIM

```TypeScript
NO_VALID_SIM = 249
```

SIM卡无效。

**起始版本：** 23

<!--Device-DisconnectedReason-NO_VALID_SIM = 249--><!--Device-DisconnectedReason-NO_VALID_SIM = 249-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## RADIO_INTERNAL_ERROR

```TypeScript
RADIO_INTERNAL_ERROR = 250
```

无线电通讯内部错误。

**起始版本：** 23

<!--Device-DisconnectedReason-RADIO_INTERNAL_ERROR = 250--><!--Device-DisconnectedReason-RADIO_INTERNAL_ERROR = 250-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## NETWORK_RESP_TIMEOUT

```TypeScript
NETWORK_RESP_TIMEOUT = 251
```

网络响应超时。

**起始版本：** 23

<!--Device-DisconnectedReason-NETWORK_RESP_TIMEOUT = 251--><!--Device-DisconnectedReason-NETWORK_RESP_TIMEOUT = 251-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## NETWORK_REJECT

```TypeScript
NETWORK_REJECT = 252
```

网络拒绝。

**起始版本：** 23

<!--Device-DisconnectedReason-NETWORK_REJECT = 252--><!--Device-DisconnectedReason-NETWORK_REJECT = 252-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## RADIO_ACCESS_FAILURE

```TypeScript
RADIO_ACCESS_FAILURE = 253
```

无线电接入故障。

**起始版本：** 23

<!--Device-DisconnectedReason-RADIO_ACCESS_FAILURE = 253--><!--Device-DisconnectedReason-RADIO_ACCESS_FAILURE = 253-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## RADIO_LINK_FAILURE

```TypeScript
RADIO_LINK_FAILURE = 254
```

无线电链路故障。

**起始版本：** 23

<!--Device-DisconnectedReason-RADIO_LINK_FAILURE = 254--><!--Device-DisconnectedReason-RADIO_LINK_FAILURE = 254-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## RADIO_LINK_LOST

```TypeScript
RADIO_LINK_LOST = 255
```

无线电链路丢失。

**起始版本：** 23

<!--Device-DisconnectedReason-RADIO_LINK_LOST = 255--><!--Device-DisconnectedReason-RADIO_LINK_LOST = 255-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## RADIO_UPLINK_FAILURE

```TypeScript
RADIO_UPLINK_FAILURE = 256
```

无线电上行链路故障。

**起始版本：** 23

<!--Device-DisconnectedReason-RADIO_UPLINK_FAILURE = 256--><!--Device-DisconnectedReason-RADIO_UPLINK_FAILURE = 256-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## RADIO_SETUP_FAILURE

```TypeScript
RADIO_SETUP_FAILURE = 257
```

无线电通讯设置失败。

**起始版本：** 23

<!--Device-DisconnectedReason-RADIO_SETUP_FAILURE = 257--><!--Device-DisconnectedReason-RADIO_SETUP_FAILURE = 257-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## RADIO_RELEASE_NORMAL

```TypeScript
RADIO_RELEASE_NORMAL = 258
```

无线电释放正常。

**起始版本：** 23

<!--Device-DisconnectedReason-RADIO_RELEASE_NORMAL = 258--><!--Device-DisconnectedReason-RADIO_RELEASE_NORMAL = 258-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## RADIO_RELEASE_ABNORMAL

```TypeScript
RADIO_RELEASE_ABNORMAL = 259
```

无线电释放异常。

**起始版本：** 23

<!--Device-DisconnectedReason-RADIO_RELEASE_ABNORMAL = 259--><!--Device-DisconnectedReason-RADIO_RELEASE_ABNORMAL = 259-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## ACCESS_CLASS_BLOCKED

```TypeScript
ACCESS_CLASS_BLOCKED = 260
```

访问类被阻止。

**起始版本：** 23

<!--Device-DisconnectedReason-ACCESS_CLASS_BLOCKED = 260--><!--Device-DisconnectedReason-ACCESS_CLASS_BLOCKED = 260-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## NETWORK_DETACH

```TypeScript
NETWORK_DETACH = 261
```

网络分离。

**起始版本：** 23

<!--Device-DisconnectedReason-NETWORK_DETACH = 261--><!--Device-DisconnectedReason-NETWORK_DETACH = 261-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## INVALID_PARAMETER

```TypeScript
INVALID_PARAMETER = 1025
```

无效参数。

**起始版本：** 23

<!--Device-DisconnectedReason-INVALID_PARAMETER = 1025--><!--Device-DisconnectedReason-INVALID_PARAMETER = 1025-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## SIM_NOT_EXIT

```TypeScript
SIM_NOT_EXIT = 1026
```

SIM卡未退出。

**起始版本：** 23

<!--Device-DisconnectedReason-SIM_NOT_EXIT = 1026--><!--Device-DisconnectedReason-SIM_NOT_EXIT = 1026-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## SIM_PIN_NEED

```TypeScript
SIM_PIN_NEED = 1027
```

需要SIM卡PIN码。

**起始版本：** 23

<!--Device-DisconnectedReason-SIM_PIN_NEED = 1027--><!--Device-DisconnectedReason-SIM_PIN_NEED = 1027-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## CALL_NOT_ALLOW

```TypeScript
CALL_NOT_ALLOW = 1029
```

不允许呼叫。

**起始版本：** 23

<!--Device-DisconnectedReason-CALL_NOT_ALLOW = 1029--><!--Device-DisconnectedReason-CALL_NOT_ALLOW = 1029-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## SIM_INVALID

```TypeScript
SIM_INVALID = 1045
```

SIM卡无效。

**起始版本：** 23

<!--Device-DisconnectedReason-SIM_INVALID = 1045--><!--Device-DisconnectedReason-SIM_INVALID = 1045-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

## UNKNOWN

```TypeScript
UNKNOWN = 1279
```

未知原因。

**起始版本：** 23

<!--Device-DisconnectedReason-UNKNOWN = 1279--><!--Device-DisconnectedReason-UNKNOWN = 1279-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

