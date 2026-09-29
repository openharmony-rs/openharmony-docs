# DisconnectedReason (System API)

```TypeScript
export enum DisconnectedReason
```

Enumerates call disconnection causes.

**Since:** 8

<!--Device-call-export enum DisconnectedReason--><!--Device-call-export enum DisconnectedReason-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## UNASSIGNED_NUMBER

```TypeScript
UNASSIGNED_NUMBER = 1
```

Unallocated (unassigned) number.

**Since:** 8

<!--Device-DisconnectedReason-UNASSIGNED_NUMBER = 1--><!--Device-DisconnectedReason-UNASSIGNED_NUMBER = 1-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## NO_ROUTE_TO_DESTINATION

```TypeScript
NO_ROUTE_TO_DESTINATION = 3
```

No route to destination.

**Since:** 8

<!--Device-DisconnectedReason-NO_ROUTE_TO_DESTINATION = 3--><!--Device-DisconnectedReason-NO_ROUTE_TO_DESTINATION = 3-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## CHANNEL_UNACCEPTABLE

```TypeScript
CHANNEL_UNACCEPTABLE = 6
```

Channel unacceptable.

**Since:** 8

<!--Device-DisconnectedReason-CHANNEL_UNACCEPTABLE = 6--><!--Device-DisconnectedReason-CHANNEL_UNACCEPTABLE = 6-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## OPERATOR_DETERMINED_BARRING

```TypeScript
OPERATOR_DETERMINED_BARRING = 8
```

Operator determined barring (ODB).

**Since:** 8

<!--Device-DisconnectedReason-OPERATOR_DETERMINED_BARRING = 8--><!--Device-DisconnectedReason-OPERATOR_DETERMINED_BARRING = 8-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## CALL_COMPLETED_ELSEWHERE

```TypeScript
CALL_COMPLETED_ELSEWHERE = 13
```

Call completed elsewhere.

**Since:** 9

<!--Device-DisconnectedReason-CALL_COMPLETED_ELSEWHERE = 13--><!--Device-DisconnectedReason-CALL_COMPLETED_ELSEWHERE = 13-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## NORMAL_CALL_CLEARING

```TypeScript
NORMAL_CALL_CLEARING = 16
```

Normal call clearing.

**Since:** 8

<!--Device-DisconnectedReason-NORMAL_CALL_CLEARING = 16--><!--Device-DisconnectedReason-NORMAL_CALL_CLEARING = 16-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## USER_BUSY

```TypeScript
USER_BUSY = 17
```

User busy.

**Since:** 8

<!--Device-DisconnectedReason-USER_BUSY = 17--><!--Device-DisconnectedReason-USER_BUSY = 17-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## NO_USER_RESPONDING

```TypeScript
NO_USER_RESPONDING = 18
```

No user responding.

**Since:** 8

<!--Device-DisconnectedReason-NO_USER_RESPONDING = 18--><!--Device-DisconnectedReason-NO_USER_RESPONDING = 18-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## USER_ALERTING_NO_ANSWER

```TypeScript
USER_ALERTING_NO_ANSWER = 19
```

User alerting, no answer.

**Since:** 8

<!--Device-DisconnectedReason-USER_ALERTING_NO_ANSWER = 19--><!--Device-DisconnectedReason-USER_ALERTING_NO_ANSWER = 19-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## CALL_REJECTED

```TypeScript
CALL_REJECTED = 21
```

Call rejected.

**Since:** 8

<!--Device-DisconnectedReason-CALL_REJECTED = 21--><!--Device-DisconnectedReason-CALL_REJECTED = 21-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## NUMBER_CHANGED

```TypeScript
NUMBER_CHANGED = 22
```

Number changed.

**Since:** 8

<!--Device-DisconnectedReason-NUMBER_CHANGED = 22--><!--Device-DisconnectedReason-NUMBER_CHANGED = 22-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## CALL_REJECTED_DUE_TO_FEATURE_AT_THE_DESTINATION

```TypeScript
CALL_REJECTED_DUE_TO_FEATURE_AT_THE_DESTINATION = 24
```

Call rejected due to reasons of the destination, for example, activation of Anonymous Call Rejection.

**Since:** 9

<!--Device-DisconnectedReason-CALL_REJECTED_DUE_TO_FEATURE_AT_THE_DESTINATION = 24--><!--Device-DisconnectedReason-CALL_REJECTED_DUE_TO_FEATURE_AT_THE_DESTINATION = 24-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## FAILED_PRE_EMPTION

```TypeScript
FAILED_PRE_EMPTION = 25
```

Failed preemption.

**Since:** 9

<!--Device-DisconnectedReason-FAILED_PRE_EMPTION = 25--><!--Device-DisconnectedReason-FAILED_PRE_EMPTION = 25-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## NON_SELECTED_USER_CLEARING

```TypeScript
NON_SELECTED_USER_CLEARING = 26
```

Non-selected user clearing.

**Since:** 9

<!--Device-DisconnectedReason-NON_SELECTED_USER_CLEARING = 26--><!--Device-DisconnectedReason-NON_SELECTED_USER_CLEARING = 26-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## DESTINATION_OUT_OF_ORDER

```TypeScript
DESTINATION_OUT_OF_ORDER = 27
```

Destination out of order.

**Since:** 8

<!--Device-DisconnectedReason-DESTINATION_OUT_OF_ORDER = 27--><!--Device-DisconnectedReason-DESTINATION_OUT_OF_ORDER = 27-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## INVALID_NUMBER_FORMAT

```TypeScript
INVALID_NUMBER_FORMAT = 28
```

Invalid number format (incomplete number).

**Since:** 8

<!--Device-DisconnectedReason-INVALID_NUMBER_FORMAT = 28--><!--Device-DisconnectedReason-INVALID_NUMBER_FORMAT = 28-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## FACILITY_REJECTED

```TypeScript
FACILITY_REJECTED = 29
```

Facility rejected.

**Since:** 9

<!--Device-DisconnectedReason-FACILITY_REJECTED = 29--><!--Device-DisconnectedReason-FACILITY_REJECTED = 29-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## RESPONSE_TO_STATUS_ENQUIRY

```TypeScript
RESPONSE_TO_STATUS_ENQUIRY = 30
```

Response to status enquiry.

**Since:** 9

<!--Device-DisconnectedReason-RESPONSE_TO_STATUS_ENQUIRY = 30--><!--Device-DisconnectedReason-RESPONSE_TO_STATUS_ENQUIRY = 30-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## NORMAL_UNSPECIFIED

```TypeScript
NORMAL_UNSPECIFIED = 31
```

Normal, unspecified.

**Since:** 9

<!--Device-DisconnectedReason-NORMAL_UNSPECIFIED = 31--><!--Device-DisconnectedReason-NORMAL_UNSPECIFIED = 31-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## NO_CIRCUIT_CHANNEL_AVAILABLE

```TypeScript
NO_CIRCUIT_CHANNEL_AVAILABLE = 34
```

No circuit/channel available.

**Since:** 9

<!--Device-DisconnectedReason-NO_CIRCUIT_CHANNEL_AVAILABLE = 34--><!--Device-DisconnectedReason-NO_CIRCUIT_CHANNEL_AVAILABLE = 34-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## NETWORK_OUT_OF_ORDER

```TypeScript
NETWORK_OUT_OF_ORDER = 38
```

Network fault.

**Since:** 8

<!--Device-DisconnectedReason-NETWORK_OUT_OF_ORDER = 38--><!--Device-DisconnectedReason-NETWORK_OUT_OF_ORDER = 38-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## TEMPORARY_FAILURE

```TypeScript
TEMPORARY_FAILURE = 41
```

Temporary failure.

**Since:** 8

<!--Device-DisconnectedReason-TEMPORARY_FAILURE = 41--><!--Device-DisconnectedReason-TEMPORARY_FAILURE = 41-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## SWITCHING_EQUIPMENT_CONGESTION

```TypeScript
SWITCHING_EQUIPMENT_CONGESTION = 42
```

Switching equipment congestion.

**Since:** 9

<!--Device-DisconnectedReason-SWITCHING_EQUIPMENT_CONGESTION = 42--><!--Device-DisconnectedReason-SWITCHING_EQUIPMENT_CONGESTION = 42-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## ACCESS_INFORMATION_DISCARDED

```TypeScript
ACCESS_INFORMATION_DISCARDED = 43
```

Access information discarded.

**Since:** 9

<!--Device-DisconnectedReason-ACCESS_INFORMATION_DISCARDED = 43--><!--Device-DisconnectedReason-ACCESS_INFORMATION_DISCARDED = 43-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## REQUEST_CIRCUIT_CHANNEL_NOT_AVAILABLE

```TypeScript
REQUEST_CIRCUIT_CHANNEL_NOT_AVAILABLE = 44
```

Requested circuit/channel unavailable.

**Since:** 9

<!--Device-DisconnectedReason-REQUEST_CIRCUIT_CHANNEL_NOT_AVAILABLE = 44--><!--Device-DisconnectedReason-REQUEST_CIRCUIT_CHANNEL_NOT_AVAILABLE = 44-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## RESOURCES_UNAVAILABLE_UNSPECIFIED

```TypeScript
RESOURCES_UNAVAILABLE_UNSPECIFIED = 47
```

Resources unavailable, unspecified.

**Since:** 9

<!--Device-DisconnectedReason-RESOURCES_UNAVAILABLE_UNSPECIFIED = 47--><!--Device-DisconnectedReason-RESOURCES_UNAVAILABLE_UNSPECIFIED = 47-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## QUALITY_OF_SERVICE_UNAVAILABLE

```TypeScript
QUALITY_OF_SERVICE_UNAVAILABLE = 49
```

QoS unavailable.

**Since:** 9

<!--Device-DisconnectedReason-QUALITY_OF_SERVICE_UNAVAILABLE = 49--><!--Device-DisconnectedReason-QUALITY_OF_SERVICE_UNAVAILABLE = 49-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## REQUESTED_FACILITY_NOT_SUBSCRIBED

```TypeScript
REQUESTED_FACILITY_NOT_SUBSCRIBED = 50
```

Requested facility not subscribed.

**Since:** 9

<!--Device-DisconnectedReason-REQUESTED_FACILITY_NOT_SUBSCRIBED = 50--><!--Device-DisconnectedReason-REQUESTED_FACILITY_NOT_SUBSCRIBED = 50-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## INCOMING_CALLS_BARRED_WITHIN_THE_CUG

```TypeScript
INCOMING_CALLS_BARRED_WITHIN_THE_CUG = 55
```

Incoming calls barred within the CUG.

**Since:** 9

<!--Device-DisconnectedReason-INCOMING_CALLS_BARRED_WITHIN_THE_CUG = 55--><!--Device-DisconnectedReason-INCOMING_CALLS_BARRED_WITHIN_THE_CUG = 55-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## BEARER_CAPABILITY_NOT_AUTHORIZED

```TypeScript
BEARER_CAPABILITY_NOT_AUTHORIZED = 57
```

Bearer capability not authorized.

**Since:** 9

<!--Device-DisconnectedReason-BEARER_CAPABILITY_NOT_AUTHORIZED = 57--><!--Device-DisconnectedReason-BEARER_CAPABILITY_NOT_AUTHORIZED = 57-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## BEARER_CAPABILITY_NOT_PRESENTLY_AVAILABLE

```TypeScript
BEARER_CAPABILITY_NOT_PRESENTLY_AVAILABLE = 58
```

Bearer capability presently available.

**Since:** 9

<!--Device-DisconnectedReason-BEARER_CAPABILITY_NOT_PRESENTLY_AVAILABLE = 58--><!--Device-DisconnectedReason-BEARER_CAPABILITY_NOT_PRESENTLY_AVAILABLE = 58-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## SERVICE_OR_OPTION_NOT_AVAILABLE_UNSPECIFIED

```TypeScript
SERVICE_OR_OPTION_NOT_AVAILABLE_UNSPECIFIED = 63
```

Service or option not available, unspecified.

**Since:** 9

<!--Device-DisconnectedReason-SERVICE_OR_OPTION_NOT_AVAILABLE_UNSPECIFIED = 63--><!--Device-DisconnectedReason-SERVICE_OR_OPTION_NOT_AVAILABLE_UNSPECIFIED = 63-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## BEARER_SERVICE_NOT_IMPLEMENTED

```TypeScript
BEARER_SERVICE_NOT_IMPLEMENTED = 65
```

Bearer service not implemented.

**Since:** 9

<!--Device-DisconnectedReason-BEARER_SERVICE_NOT_IMPLEMENTED = 65--><!--Device-DisconnectedReason-BEARER_SERVICE_NOT_IMPLEMENTED = 65-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## ACM_EQUALTO_OR_GREATER_THAN_THE_MAXIMUM_VALUE

```TypeScript
ACM_EQUALTO_OR_GREATER_THAN_THE_MAXIMUM_VALUE = 68
```

ACM greater than or equal to the maximum value.

**Since:** 9

<!--Device-DisconnectedReason-ACM_EQUALTO_OR_GREATER_THAN_THE_MAXIMUM_VALUE = 68--><!--Device-DisconnectedReason-ACM_EQUALTO_OR_GREATER_THAN_THE_MAXIMUM_VALUE = 68-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## REQUESTED_FACILITY_NOT_IMPLEMENTED

```TypeScript
REQUESTED_FACILITY_NOT_IMPLEMENTED = 69
```

Requested facility not implemented.

**Since:** 9

<!--Device-DisconnectedReason-REQUESTED_FACILITY_NOT_IMPLEMENTED = 69--><!--Device-DisconnectedReason-REQUESTED_FACILITY_NOT_IMPLEMENTED = 69-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## ONLY_RESTRICTED_DIGITAL_INFO_BEARER_CAPABILITY_IS_AVAILABLE

```TypeScript
ONLY_RESTRICTED_DIGITAL_INFO_BEARER_CAPABILITY_IS_AVAILABLE = 70
```

Only restricted digital information bearer capability available.

**Since:** 9

<!--Device-DisconnectedReason-ONLY_RESTRICTED_DIGITAL_INFO_BEARER_CAPABILITY_IS_AVAILABLE = 70--><!--Device-DisconnectedReason-ONLY_RESTRICTED_DIGITAL_INFO_BEARER_CAPABILITY_IS_AVAILABLE = 70-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## SERVICE_OR_OPTION_NOT_IMPLEMENTED_UNSPECIFIED

```TypeScript
SERVICE_OR_OPTION_NOT_IMPLEMENTED_UNSPECIFIED = 79
```

Service or option not implemented, unspecified.

**Since:** 9

<!--Device-DisconnectedReason-SERVICE_OR_OPTION_NOT_IMPLEMENTED_UNSPECIFIED = 79--><!--Device-DisconnectedReason-SERVICE_OR_OPTION_NOT_IMPLEMENTED_UNSPECIFIED = 79-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## INVALID_TRANSACTION_IDENTIFIER_VALUE

```TypeScript
INVALID_TRANSACTION_IDENTIFIER_VALUE = 81
```

Invalid transaction identifier value.

**Since:** 9

<!--Device-DisconnectedReason-INVALID_TRANSACTION_IDENTIFIER_VALUE = 81--><!--Device-DisconnectedReason-INVALID_TRANSACTION_IDENTIFIER_VALUE = 81-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## USER_NOT_MEMBER_OF_CUG

```TypeScript
USER_NOT_MEMBER_OF_CUG = 87
```

User not member of CUG.

**Since:** 9

<!--Device-DisconnectedReason-USER_NOT_MEMBER_OF_CUG = 87--><!--Device-DisconnectedReason-USER_NOT_MEMBER_OF_CUG = 87-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## INCOMPATIBLE_DESTINATION

```TypeScript
INCOMPATIBLE_DESTINATION = 88
```

Incompatible destination.

**Since:** 9

<!--Device-DisconnectedReason-INCOMPATIBLE_DESTINATION = 88--><!--Device-DisconnectedReason-INCOMPATIBLE_DESTINATION = 88-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## INVALID_TRANSIT_NETWORK_SELECTION

```TypeScript
INVALID_TRANSIT_NETWORK_SELECTION = 91
```

Invalid transit network selection.

**Since:** 9

<!--Device-DisconnectedReason-INVALID_TRANSIT_NETWORK_SELECTION = 91--><!--Device-DisconnectedReason-INVALID_TRANSIT_NETWORK_SELECTION = 91-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## SEMANTICALLY_INCORRECT_MESSAGE

```TypeScript
SEMANTICALLY_INCORRECT_MESSAGE = 95
```

Semantically incorrect message.

**Since:** 9

<!--Device-DisconnectedReason-SEMANTICALLY_INCORRECT_MESSAGE = 95--><!--Device-DisconnectedReason-SEMANTICALLY_INCORRECT_MESSAGE = 95-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## INVALID_MANDATORY_INFORMATION

```TypeScript
INVALID_MANDATORY_INFORMATION = 96
```

Invalid mandatory information.

**Since:** 9

<!--Device-DisconnectedReason-INVALID_MANDATORY_INFORMATION = 96--><!--Device-DisconnectedReason-INVALID_MANDATORY_INFORMATION = 96-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## MESSAGE_TYPE_NON_EXISTENT_OR_NOT_IMPLEMENTED

```TypeScript
MESSAGE_TYPE_NON_EXISTENT_OR_NOT_IMPLEMENTED = 97
```

Message type non-existent or not implemented.

**Since:** 9

<!--Device-DisconnectedReason-MESSAGE_TYPE_NON_EXISTENT_OR_NOT_IMPLEMENTED = 97--><!--Device-DisconnectedReason-MESSAGE_TYPE_NON_EXISTENT_OR_NOT_IMPLEMENTED = 97-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## MESSAGE_TYPE_NOT_COMPATIBLE_WITH_PROTOCOL_STATE

```TypeScript
MESSAGE_TYPE_NOT_COMPATIBLE_WITH_PROTOCOL_STATE = 98
```

Message type not compatible with protocol state.

**Since:** 9

<!--Device-DisconnectedReason-MESSAGE_TYPE_NOT_COMPATIBLE_WITH_PROTOCOL_STATE = 98--><!--Device-DisconnectedReason-MESSAGE_TYPE_NOT_COMPATIBLE_WITH_PROTOCOL_STATE = 98-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## INFORMATION_ELEMENT_NON_EXISTENT_OR_NOT_IMPLEMENTED

```TypeScript
INFORMATION_ELEMENT_NON_EXISTENT_OR_NOT_IMPLEMENTED = 99
```

IE non-existent or not implemented.

**Since:** 9

<!--Device-DisconnectedReason-INFORMATION_ELEMENT_NON_EXISTENT_OR_NOT_IMPLEMENTED = 99--><!--Device-DisconnectedReason-INFORMATION_ELEMENT_NON_EXISTENT_OR_NOT_IMPLEMENTED = 99-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## CONDITIONAL_IE_ERROR

```TypeScript
CONDITIONAL_IE_ERROR = 100
```

Conditional IE error.

**Since:** 9

<!--Device-DisconnectedReason-CONDITIONAL_IE_ERROR = 100--><!--Device-DisconnectedReason-CONDITIONAL_IE_ERROR = 100-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## MESSAGE_NOT_COMPATIBLE_WITH_PROTOCOL_STATE

```TypeScript
MESSAGE_NOT_COMPATIBLE_WITH_PROTOCOL_STATE = 101
```

Message not compatible with protocol state.

**Since:** 9

<!--Device-DisconnectedReason-MESSAGE_NOT_COMPATIBLE_WITH_PROTOCOL_STATE = 101--><!--Device-DisconnectedReason-MESSAGE_NOT_COMPATIBLE_WITH_PROTOCOL_STATE = 101-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## RECOVERY_ON_TIMER_EXPIRED

```TypeScript
RECOVERY_ON_TIMER_EXPIRED = 102
```

Recovery on timer expiry.

**Since:** 9

<!--Device-DisconnectedReason-RECOVERY_ON_TIMER_EXPIRED = 102--><!--Device-DisconnectedReason-RECOVERY_ON_TIMER_EXPIRED = 102-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## PROTOCOL_ERROR_UNSPECIFIED

```TypeScript
PROTOCOL_ERROR_UNSPECIFIED = 111
```

Protocol error, unspecified.

**Since:** 9

<!--Device-DisconnectedReason-PROTOCOL_ERROR_UNSPECIFIED = 111--><!--Device-DisconnectedReason-PROTOCOL_ERROR_UNSPECIFIED = 111-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## INTERWORKING_UNSPECIFIED

```TypeScript
INTERWORKING_UNSPECIFIED = 127
```

Interworking, unspecified.

**Since:** 9

<!--Device-DisconnectedReason-INTERWORKING_UNSPECIFIED = 127--><!--Device-DisconnectedReason-INTERWORKING_UNSPECIFIED = 127-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## CALL_BARRED

```TypeScript
CALL_BARRED = 240
```

Call barred.

**Since:** 9

<!--Device-DisconnectedReason-CALL_BARRED = 240--><!--Device-DisconnectedReason-CALL_BARRED = 240-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## FDN_BLOCKED

```TypeScript
FDN_BLOCKED = 241
```

FDN blocked.

**Since:** 9

<!--Device-DisconnectedReason-FDN_BLOCKED = 241--><!--Device-DisconnectedReason-FDN_BLOCKED = 241-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## IMSI_UNKNOWN_IN_VLR

```TypeScript
IMSI_UNKNOWN_IN_VLR = 242
```

IMSI unknown in VLR.

**Since:** 9

<!--Device-DisconnectedReason-IMSI_UNKNOWN_IN_VLR = 242--><!--Device-DisconnectedReason-IMSI_UNKNOWN_IN_VLR = 242-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## IMEI_NOT_ACCEPTED

```TypeScript
IMEI_NOT_ACCEPTED = 243
```

IMEI not accepted.

**Since:** 9

<!--Device-DisconnectedReason-IMEI_NOT_ACCEPTED = 243--><!--Device-DisconnectedReason-IMEI_NOT_ACCEPTED = 243-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## DIAL_MODIFIED_TO_USSD

```TypeScript
DIAL_MODIFIED_TO_USSD = 244
```

Dial request modified to USSD request.

**Since:** 9

<!--Device-DisconnectedReason-DIAL_MODIFIED_TO_USSD = 244--><!--Device-DisconnectedReason-DIAL_MODIFIED_TO_USSD = 244-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## DIAL_MODIFIED_TO_SS

```TypeScript
DIAL_MODIFIED_TO_SS = 245
```

Dial request modified to SS request.

**Since:** 9

<!--Device-DisconnectedReason-DIAL_MODIFIED_TO_SS = 245--><!--Device-DisconnectedReason-DIAL_MODIFIED_TO_SS = 245-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## DIAL_MODIFIED_TO_DIAL

```TypeScript
DIAL_MODIFIED_TO_DIAL = 246
```

Dial request modified to dial with different number.

**Since:** 9

<!--Device-DisconnectedReason-DIAL_MODIFIED_TO_DIAL = 246--><!--Device-DisconnectedReason-DIAL_MODIFIED_TO_DIAL = 246-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## RADIO_OFF

```TypeScript
RADIO_OFF = 247
```

Radio off.

**Since:** 9

<!--Device-DisconnectedReason-RADIO_OFF = 247--><!--Device-DisconnectedReason-RADIO_OFF = 247-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## OUT_OF_SERVICE

```TypeScript
OUT_OF_SERVICE = 248
```

Stops the service.

**Since:** 9

<!--Device-DisconnectedReason-OUT_OF_SERVICE = 248--><!--Device-DisconnectedReason-OUT_OF_SERVICE = 248-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## NO_VALID_SIM

```TypeScript
NO_VALID_SIM = 249
```

No valid SIM.

**Since:** 9

<!--Device-DisconnectedReason-NO_VALID_SIM = 249--><!--Device-DisconnectedReason-NO_VALID_SIM = 249-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## RADIO_INTERNAL_ERROR

```TypeScript
RADIO_INTERNAL_ERROR = 250
```

Radio internal error.

**Since:** 9

<!--Device-DisconnectedReason-RADIO_INTERNAL_ERROR = 250--><!--Device-DisconnectedReason-RADIO_INTERNAL_ERROR = 250-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## NETWORK_RESP_TIMEOUT

```TypeScript
NETWORK_RESP_TIMEOUT = 251
```

Network response timeout.

**Since:** 9

<!--Device-DisconnectedReason-NETWORK_RESP_TIMEOUT = 251--><!--Device-DisconnectedReason-NETWORK_RESP_TIMEOUT = 251-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## NETWORK_REJECT

```TypeScript
NETWORK_REJECT = 252
```

Request rejected by network.

**Since:** 9

<!--Device-DisconnectedReason-NETWORK_REJECT = 252--><!--Device-DisconnectedReason-NETWORK_REJECT = 252-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## RADIO_ACCESS_FAILURE

```TypeScript
RADIO_ACCESS_FAILURE = 253
```

Radio access failure.

**Since:** 9

<!--Device-DisconnectedReason-RADIO_ACCESS_FAILURE = 253--><!--Device-DisconnectedReason-RADIO_ACCESS_FAILURE = 253-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## RADIO_LINK_FAILURE

```TypeScript
RADIO_LINK_FAILURE = 254
```

Radio link failure.

**Since:** 9

<!--Device-DisconnectedReason-RADIO_LINK_FAILURE = 254--><!--Device-DisconnectedReason-RADIO_LINK_FAILURE = 254-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## RADIO_LINK_LOST

```TypeScript
RADIO_LINK_LOST = 255
```

Radio link lost.

**Since:** 9

<!--Device-DisconnectedReason-RADIO_LINK_LOST = 255--><!--Device-DisconnectedReason-RADIO_LINK_LOST = 255-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## RADIO_UPLINK_FAILURE

```TypeScript
RADIO_UPLINK_FAILURE = 256
```

Radio uplink failure.

**Since:** 9

<!--Device-DisconnectedReason-RADIO_UPLINK_FAILURE = 256--><!--Device-DisconnectedReason-RADIO_UPLINK_FAILURE = 256-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## RADIO_SETUP_FAILURE

```TypeScript
RADIO_SETUP_FAILURE = 257
```

Radio setup failure.

**Since:** 9

<!--Device-DisconnectedReason-RADIO_SETUP_FAILURE = 257--><!--Device-DisconnectedReason-RADIO_SETUP_FAILURE = 257-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## RADIO_RELEASE_NORMAL

```TypeScript
RADIO_RELEASE_NORMAL = 258
```

Radio release normal.

**Since:** 9

<!--Device-DisconnectedReason-RADIO_RELEASE_NORMAL = 258--><!--Device-DisconnectedReason-RADIO_RELEASE_NORMAL = 258-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## RADIO_RELEASE_ABNORMAL

```TypeScript
RADIO_RELEASE_ABNORMAL = 259
```

Radio release abnormal.

**Since:** 9

<!--Device-DisconnectedReason-RADIO_RELEASE_ABNORMAL = 259--><!--Device-DisconnectedReason-RADIO_RELEASE_ABNORMAL = 259-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## ACCESS_CLASS_BLOCKED

```TypeScript
ACCESS_CLASS_BLOCKED = 260
```

Access class blocked.

**Since:** 9

<!--Device-DisconnectedReason-ACCESS_CLASS_BLOCKED = 260--><!--Device-DisconnectedReason-ACCESS_CLASS_BLOCKED = 260-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## NETWORK_DETACH

```TypeScript
NETWORK_DETACH = 261
```

Network detached.

**Since:** 9

<!--Device-DisconnectedReason-NETWORK_DETACH = 261--><!--Device-DisconnectedReason-NETWORK_DETACH = 261-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## INVALID_PARAMETER

```TypeScript
INVALID_PARAMETER = 1025
```

Invalid parameter.

**Since:** 8

<!--Device-DisconnectedReason-INVALID_PARAMETER = 1025--><!--Device-DisconnectedReason-INVALID_PARAMETER = 1025-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## SIM_NOT_EXIT

```TypeScript
SIM_NOT_EXIT = 1026
```

SIM not exit.

**Since:** 8

<!--Device-DisconnectedReason-SIM_NOT_EXIT = 1026--><!--Device-DisconnectedReason-SIM_NOT_EXIT = 1026-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## SIM_PIN_NEED

```TypeScript
SIM_PIN_NEED = 1027
```

SIM PIN needed.

**Since:** 8

<!--Device-DisconnectedReason-SIM_PIN_NEED = 1027--><!--Device-DisconnectedReason-SIM_PIN_NEED = 1027-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## CALL_NOT_ALLOW

```TypeScript
CALL_NOT_ALLOW = 1029
```

Call not allowed.

**Since:** 8

<!--Device-DisconnectedReason-CALL_NOT_ALLOW = 1029--><!--Device-DisconnectedReason-CALL_NOT_ALLOW = 1029-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## SIM_INVALID

```TypeScript
SIM_INVALID = 1045
```

No valid SIM.

**Since:** 8

<!--Device-DisconnectedReason-SIM_INVALID = 1045--><!--Device-DisconnectedReason-SIM_INVALID = 1045-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

## UNKNOWN

```TypeScript
UNKNOWN = 1279
```

Unknown reason.

**Since:** 8

<!--Device-DisconnectedReason-UNKNOWN = 1279--><!--Device-DisconnectedReason-UNKNOWN = 1279-End-->

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.
