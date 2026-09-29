# telephony_radio.h

## Overview

Provides C interface for the telephony radio.

**Include**: <telephony/core_service/telephony_radio_type.h>

**Library**: libtelephony_radio.so

**Since**: 13

**Related module**: [](capi-.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [Telephony_RadioResult OH_Telephony_GetNetworkState(Telephony_NetworkState *state)](#oh_telephony_getnetworkstate) | Obtains the network status. |

## Function description

### OH_Telephony_GetNetworkState()

```c
Telephony_RadioResult OH_Telephony_GetNetworkState(Telephony_NetworkState *state)
```

**Description**

Obtains the network status.

**Required permission**: ohos.permission.GET_NETWORK_INFO

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Telephony_NetworkState](capi--telephony-networkstate.md) *state | Structure of the network status information received by the user. |

**Returns**:

| Type | Description |
| -- | -- |
| [Telephony_RadioResult](capi-telephony-radio-type-h.md#telephony_radioresult) | Result code. For details, see [Telephony_RadioResult](capi-telephony-radio-type-h.md#telephony_radioresult). <br>[TEL_RADIO_SUCCESS](capi-telephony-radio-type-h.md#telephony_radioresult): Operation succeeded. <br>[TEL_RADIO_PERMISSION_DENIED](capi-telephony-radio-type-h.md#telephony_radioresult): Permission denied. <br>[TEL_RADIO_ERR_MARSHALLING_FAILED](capi-telephony-radio-type-h.md#telephony_radioresult): Marshalling failed. <br>[TEL_RADIO_ERR_SERVICE_CONNECTION_FAILED](capi-telephony-radio-type-h.md#telephony_radioresult): Telephony service connection failed. <br>[TEL_RADIO_ERR_OPERATION_FAILED](capi-telephony-radio-type-h.md#telephony_radioresult): Telephony service operation failed. <br>[TEL_RADIO_ERR_INVALID_PARAM](capi-telephony-radio-type-h.md#telephony_radioresult): Invalid parameter. |


