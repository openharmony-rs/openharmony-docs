# oh_wifi.h

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @qq_43802146-->
<!--Designer: @qq_43802146-->
<!--Tester: @furryfurry123-->
<!--Adviser: @zhang_yixin13-->
## Overview

Defines APIs for obtaining Wi-Fi switch state.

**File to include**: <ConnectivityKit/wifi/oh_wifi.h>

**Library**: libwifi_ndk.so

**System capability**: SystemCapability.Communication.WiFi.STA

**Since**: 13

**Related module**: [Wifi](capi-wifi.md)

## Summary

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [Wifi_ResultCode](#wifi_resultcode) | Wifi_ResultCode | Enumerates the error codes returned by Wi-Fi APIs.|

### Functions

| Name| Description|
| -- | -- |
| [Wifi_ResultCode OH_Wifi_IsWifiEnabled(bool *enabled)](#oh_wifi_iswifienabled) | Checks whether Wi-Fi is enabled.|
| [Wifi_ResultCode OH_Wifi_GetDeviceMacAddress(char *macAddr, unsigned int *macAddrLen)](#oh_wifi_getdevicemacaddress) | Obtains the actual MAC address of a device.|

## Enum Description

### Wifi_ResultCode

```
enum Wifi_ResultCode
```

**Description**

Enumerates the error codes returned by Wi-Fi APIs.

**Since**: 13

| Enum Item| Description|
| -- | -- |
| WIFI_SUCCESS = 0 | Operation success.|
| WIFI_PERMISSION_DENIED = 201 | Permission verification fails.|
| WIFI_INVALID_PARAM = 401 | Invalid parameter.<br> Possible causes: 1. The input parameter is a null pointer. 2. The parameter value is out of the value range.|
| WIFI_NOT_SUPPORTED = 801 | Function not supported. due to limited device capabilities.|
| WIFI_OPERATION_FAILED = 2501000 | Operation failed.<br> Possible cause: The internal execution of the service fails.|
| WIFI_STA_DISABLED = 2501001 | STA service not started.<br> Possible cause: Wi-Fi is disabled.|


## Function Description

### OH_Wifi_IsWifiEnabled()

```
Wifi_ResultCode OH_Wifi_IsWifiEnabled(bool *enabled)
```

**Description**

Checks whether Wi-Fi is enabled.

**Since**: 13

**Parameters**

| Name| Description|
| -- | -- |
| bool *enabled | Pointer to the boolean value indicating the Wi-Fi state.<br> The value **true** indicates that Wi-Fi is enabled, and the value **false** indicates the opposite.<br> A null pointer is prohibited. If a null pointer is passed in, an error is returned.|

**Returns**

| Type| Description|
| -- | -- |
| [Wifi_ResultCode](capi-oh-wifi-h.md#wifi_resultcode) | Operation result, which is specified by [Wifi_ResultCode](capi-oh-wifi-h.md#wifi_resultcode). The value can be:<br>     [WIFI_SUCCESS](capi-oh-wifi-h.md#wifi_resultcode): The Wi-Fi switch status is obtained successfully.<br>     [WIFI_INVALID_PARAM](capi-oh-wifi-h.md#wifi_resultcode): The input parameter is a null pointer.<br>     [WIFI_OPERATION_FAILED](capi-oh-wifi-h.md#wifi_resultcode): An internal error occurs during service execution.|

### OH_Wifi_GetDeviceMacAddress()

```
Wifi_ResultCode OH_Wifi_GetDeviceMacAddress(char *macAddr, unsigned int *macAddrLen)
```

**Description**

Obtains the actual MAC address of a device.

**Required permissions**: ohos.permission.GET_WIFI_LOCAL_MAC and ohos.permission.GET_WIFI_INFO

**Since**: 21

**Parameters**

| Name| Description|
| -- | -- |
| char *macAddr | Character array of the device MAC address, which ends with '\0'.|
| unsigned int *macAddrLen | Memory size allocated to **macAddr**.|

**Returns**

| Type| Description|
| -- | -- |
| [Wifi_ResultCode](capi-oh-wifi-h.md#wifi_resultcode) | Operation result, which is specified by [Wifi_ResultCode](capi-oh-wifi-h.md#wifi_resultcode). The value can be:<br>     [WIFI_SUCCESS](capi-oh-wifi-h.md#wifi_resultcode): The MAC address of the device is obtained successfully.<br>     [WIFI_PERMISSION_DENIED](capi-oh-wifi-h.md#wifi_resultcode): The permission is denied.<br>     [WIFI_NOT_SUPPORTED](capi-oh-wifi-h.md#wifi_resultcode): This capability is not supported.<br>     [WIFI_INVALID_PARAM](capi-oh-wifi-h.md#wifi_resultcode): The input **macAddr** is a null pointer.<br>     [WIFI_OPERATION_FAILED](capi-oh-wifi-h.md#wifi_resultcode): An internal error occurs during internal execution.<br>     [WIFI_STA_DISABLED](capi-oh-wifi-h.md#wifi_resultcode): The Wi-Fi STA mode is disabled.|
