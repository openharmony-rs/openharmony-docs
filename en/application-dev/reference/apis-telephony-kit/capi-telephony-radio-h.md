# telephony_radio.h
<!--Kit: Telephony Kit-->
<!--Subsystem: Telephony-->
<!--Owner: @Terence_Super-->
<!--Designer: @Terence_Super-->
<!--Tester: @jiang_99-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=8849c1ba46e94276e60aba7fd9c38f7b7dbc0634 translatedAt=2026-11-03T03:43:21.310Z pushedAt=2026-11-03T08:15:13.717Z nl=1 -->

## Overview

This module defines C APIs for the network search module and provides the capability to obtain the mobile network status (including the network registration status, carrier information, and network mode). It applies to scenarios where an app needs to query the network connection status of the current card slot.

**File to include**: <telephony/core_service/telephony_radio.h>

**Library**: libtelephony_radio.so

**System capability**: SystemCapability.Telephony.CoreService

**Since**: 13

**Related module**: [Telephony](capi-telephony.md)

## Summary

### Functions

| Name| Description|
| -- | -- |
| [Telephony_RadioResult OH_Telephony_GetNetworkState(Telephony_NetworkState *state)](#oh_telephony_getnetworkstate) | Obtains the network status.|
| [Telephony_RadioResult OH_Telephony_GetNetworkStateForSlot(int32_t slotId, Telephony_NetworkState *state)](#oh_telephony_getnetworkstateforslot) | Obtains the network status of the SIM card in the specified slot.|

## Function Description

### OH_Telephony_GetNetworkState()

```c
Telephony_RadioResult OH_Telephony_GetNetworkState(Telephony_NetworkState *state)
```

**Description**

Obtains the network status.

**System capability**: SystemCapability.Telephony.CoreService

**Required permissions**: ohos.permission.GET_NETWORK_INFO

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [Telephony_NetworkState](capi-telephony-telephony-networkstate.md) *state | Pointer to the struct used to receive network state information. |

**Returns**

| Type| Description|
| -- | -- |
| [Telephony_RadioResult](capi-telephony-radio-type-h.md#telephony_radioresult) | Result code. For details, see [Telephony_RadioResult](capi-telephony-radio-type-h.md#telephony_radioresult).<br>         [TEL_RADIO_SUCCESS](capi-telephony-radio-type-h.md#telephony_radioresult): Operation succeeded.<br>         [TEL_RADIO_PERMISSION_DENIED](capi-telephony-radio-type-h.md#telephony_radioresult): Permission denied.<br>         [TEL_RADIO_ERR_MARSHALLING_FAILED](capi-telephony-radio-type-h.md#telephony_radioresult): Marshalling failed.<br>         [TEL_RADIO_ERR_SERVICE_CONNECTION_FAILED](capi-telephony-radio-type-h.md#telephony_radioresult): Telephony service connection failed.<br>         [TEL_RADIO_ERR_OPERATION_FAILED](capi-telephony-radio-type-h.md#telephony_radioresult): Telephony service operation failed.<br>         [TEL_RADIO_ERR_INVALID_PARAM](capi-telephony-radio-type-h.md#telephony_radioresult): Invalid parameter.|

### OH_Telephony_GetNetworkStateForSlot()

```c
Telephony_RadioResult OH_Telephony_GetNetworkStateForSlot(int32_t slotId, Telephony_NetworkState *state)
```

**Description**

Obtains the network status of the SIM card in the specified slot.

**System capability**: SystemCapability.Telephony.CoreService

**Required permissions**: ohos.permission.GET_NETWORK_INFO

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| int32_t slotId | Card slot ID.|
| [Telephony_NetworkState](capi-telephony-telephony-networkstate.md) *state | Pointer to the struct used to receive network state information. |

**Returns**

| Type| Description|
| -- | -- |
| [Telephony_RadioResult](capi-telephony-radio-type-h.md#telephony_radioresult) | Result code. For details, see [Telephony_RadioResult](capi-telephony-radio-type-h.md#telephony_radioresult).<br>         [TEL_RADIO_SUCCESS](capi-telephony-radio-type-h.md#telephony_radioresult): Operation succeeded.<br>         [TEL_RADIO_PERMISSION_DENIED](capi-telephony-radio-type-h.md#telephony_radioresult): Permission denied.<br>         [TEL_RADIO_ERR_MARSHALLING_FAILED](capi-telephony-radio-type-h.md#telephony_radioresult): Marshalling failed.<br>         [TEL_RADIO_ERR_SERVICE_CONNECTION_FAILED](capi-telephony-radio-type-h.md#telephony_radioresult): Telephony service connection failed.<br>         [TEL_RADIO_ERR_OPERATION_FAILED](capi-telephony-radio-type-h.md#telephony_radioresult): Telephony service operation failed.<br>         [TEL_RADIO_ERR_INVALID_PARAM](capi-telephony-radio-type-h.md#telephony_radioresult): Invalid parameter.|


