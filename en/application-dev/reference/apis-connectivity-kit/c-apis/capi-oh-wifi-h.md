# oh_wifi.h

## Overview

Define interfaces for querying wifi switch status.

**Library**: libwifi_ndk.so

**System capability**: SystemCapability.Communication.WiFi.STA

**Since**: 13

**Related module**: [Wifi](capi-wifi.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_WifiLinkedInfo](capi-wifi-oh-wifilinkedinfo.md) | OH_WifiLinkedInfo | Represents the Wi-Fi connection information.<br> This structure describes the hotspot information of the current station connection. The information can be obtained by calling {@link OH_Wifi_GetLinkedInfo}. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [Wifi_ResultCode](#wifi_resultcode) | Wifi_ResultCode | Enumerates the wifi result codes. |
| [OH_WifiLinkType](#oh_wifilinktype) | OH_WifiLinkType | Enumerates Wi-Fi link types. |
| [OH_WifiConnState](#oh_wificonnstate) | OH_WifiConnState | Enumerates Wi-Fi connection states. |
| [OH_WifiChannelWidth](#oh_wifichannelwidth) | OH_WifiChannelWidth | Enumerates Wi-Fi channel widths. |
| [OH_WifiCategory](#oh_wificategory) | OH_WifiCategory | Wi-Fi categories. |
| [OH_WifiStandard](#oh_wifistandard) | OH_WifiStandard | Enumerates Wi-Fi standards. |

### Macro

| Name | Description |
| -- | -- |
| WIFI_MAX_SSID_LEN 33 // 32 +0 | Indicates the maximum length of a Wi-Fi SSID.<br>**Since**: 24 The maximum length is 32, and the last bit is reserved and set to <b>\0</b>. \n |
| WIFI_MAC_LEN 18 | Indicates the maximum length of a Wi-Fi MAC address or a Wi-Fi BSSID.<br>**Since**: 24 |

### Function

| Name | Description |
| -- | -- |
| [Wifi_ResultCode OH_Wifi_IsWifiEnabled(bool *enabled)](#oh_wifi_iswifienabled) | Check whether the wifi switch is enabled. |
| [Wifi_ResultCode OH_Wifi_GetDeviceMacAddress(char *macAddr, unsigned int *macAddrLen)](#oh_wifi_getdevicemacaddress) | Get the device Mac address. |
| [Wifi_ResultCode OH_Wifi_GetLinkedInfo(OH_WifiLinkedInfo *info)](#oh_wifi_getlinkedinfo) | Get wifi linked info. When macType is 1 (device MAC address), obtaining macAddress also requires the ohos.permission.GET_WIFI_LOCAL_MAC permission. This permission is available only to system apps in API versions 8–15. Starting from API 16, it is available to regular apps on PC/2-in-1 devices, while on other devices it remains restricted to system apps. If the permission is not granted, macAddress will be returned as empty. If the application has requested the ohos.permission.GET_WIFI_PEERS_MAC permission, the bssid in the returned result will be the real BSSID address; otherwise, it will be a randomized device address. |

## Enum type description

### Wifi_ResultCode

```c
enum Wifi_ResultCode
```

**Description**

Enumerates the wifi result codes.

**System capability**: SystemCapability.Communication.WiFi.STA

**Since**: 13

| Enum item | Description |
| -- | -- |
| WIFI_SUCCESS = 0 | The operation is successful. |
| WIFI_PERMISSION_DENIED = 201 | Permission verification failed. The application does not have the permission required to call the API. |
| WIFI_INVALID_PARAM = 401 | Parameter error. Possible reasons: 1. The input parameter is a null pointer; 2. Parameter values exceed the defined range. |
| WIFI_NOT_SUPPORTED = 801 | Capability not supported. Failed to call function due to limited device capabilities. |
| WIFI_OPERATION_FAILED = 2501000 | Operation failed. Possible reasons: Internal execution failed. |
| WIFI_STA_DISABLED = 2501001 |  Wi-Fi STA disabled.<br>**Since**: 21 |

### OH_WifiLinkType

```c
enum OH_WifiLinkType
```

**Description**

Enumerates Wi-Fi link types.

**System capability**: SystemCapability.Communication.WiFi.STA

**Since**: 24

| Enum item | Description |
| -- | -- |
| OH_WIFI_LINK_DISCONNECT = -1 | Not connected.<br>**Since**: 24 |
| OH_WIFI_LINK_DEFAULT_LINK = 0 | Default link.<br>**Since**: 24 |
| OH_WIFI_LINK_WIFI7_SINGLE_LINK = 1 | Wi-Fi 7 single link.<br>**Since**: 24 |
| OH_WIFI_LINK_WIFI7_MLSR = 2 | Wi-Fi 7 MLSR.<br>**Since**: 24 |
| OH_WIFI_LINK_WIFI7_EMLSR = 3 | Wi-Fi 7 EMLSR.<br>**Since**: 24 |
| OH_WIFI_LINK_WIFI7_STR = 4 | Wi-Fi 7 STR.<br>**Since**: 24 |
| OH_WIFI_LINK_WIFI7_LEGACY = 5 | Wi-Fi 7 legacy mode without MLO.<br>**Since**: 24 |

### OH_WifiConnState

```c
enum OH_WifiConnState
```

**Description**

Enumerates Wi-Fi connection states.

**System capability**: SystemCapability.Communication.WiFi.STA

**Since**: 24

| Enum item | Description |
| -- | -- |
| OH_WIFI_CONN_SCANNING | The device is searching for an available AP.<br>**Since**: 24 |
| OH_WIFI_CONN_CONNECTING | The Wi-Fi connection is being set up.<br>**Since**: 24 |
| OH_WIFI_CONN_AUTHENTICATING | The Wi-Fi connection is being authenticated.<br>**Since**: 24 |
| OH_WIFI_CONN_OBTAINING_IPADDR | The IP address of the Wi-Fi connection is being obtained.<br>**Since**: 24 |
| OH_WIFI_CONN_CONNECTED | The Wi-Fi connection has been set up.<br>**Since**: 24 |
| OH_WIFI_CONN_DISCONNECTING | The Wi-Fi connection is being torn down.<br>**Since**: 24 |
| OH_WIFI_CONN_DISCONNECTED | The Wi-Fi connection has been torn down.<br>**Since**: 24 |
| OH_WIFI_CONN_SPECIAL_CONNECT | The Wi-Fi connection is in a special state.<br>**Since**: 24 |
| OH_WIFI_CONN_UNKNOWN | Failed to set up the Wi-Fi connection.<br>**Since**: 24 |

### OH_WifiChannelWidth

```c
enum OH_WifiChannelWidth
```

**Description**

Enumerates Wi-Fi channel widths.

**System capability**: SystemCapability.Communication.WiFi.STA

**Since**: 24

| Enum item | Description |
| -- | -- |
| OH_WIFI_WIDTH_20MHZ = 0 | 20 MHz channel width.<br>**Since**: 24 |
| OH_WIFI_WIDTH_40MHZ = 1 | 40 MHz channel width.<br>**Since**: 24 |
| OH_WIFI_WIDTH_80MHZ = 2 | 80 MHz channel width.<br>**Since**: 24 |
| OH_WIFI_WIDTH_160MHZ = 3 | 160 MHz channel width.<br>**Since**: 24 |
| OH_WIFI_WIDTH_80MHZ_PLUS = 4 | 80 + 80 MHz channel width.<br>**Since**: 24 |
| OH_WIFI_WIDTH_INVALID | Invalid channel width.<br>**Since**: 24 |

### OH_WifiCategory

```c
enum OH_WifiCategory
```

**Description**

Wi-Fi categories.

**System capability**: SystemCapability.Communication.WiFi.STA

**Since**: 24

| Enum item | Description |
| -- | -- |
| OH_WIFI_CATEGORY_DEFAULT = 1 | Default category.<br>**Since**: 24 |
| OH_WIFI_CATEGORY_WIFI6 = 2 | Wi-Fi 6 category.<br>**Since**: 24 |
| OH_WIFI_CATEGORY_WIFI6_PLUS = 3 | Wi-Fi 6 plus category.<br>**Since**: 24 |
| OH_WIFI_CATEGORY_WIFI7 = 4 | Wi-Fi 7 category.<br>**Since**: 24 |
| OH_WIFI_CATEGORY_WIFI7_PLUS = 5 | Wi-Fi 7 plus category.<br>**Since**: 24 |

### OH_WifiStandard

```c
enum OH_WifiStandard
```

**Description**

Enumerates Wi-Fi standards.

**System capability**: SystemCapability.Communication.WiFi.STA

**Since**: 24

| Enum item | Description |
| -- | -- |
| OH_WIFI_STANDARD_UNDEFINED = 0 | Invalid Wi-Fi standard.<br>**Since**: 24 |
| OH_WIFI_STANDARD_11A = 1 | 802.11a Wi-Fi standard.<br>**Since**: 24 |
| OH_WIFI_STANDARD_11B = 2 | 802.11b Wi-Fi standard.<br>**Since**: 24 |
| OH_WIFI_STANDARD_11G = 3 | 802.11g Wi-Fi standard.<br>**Since**: 24 |
| OH_WIFI_STANDARD_11N = 4 | 802.11n Wi-Fi standard.<br>**Since**: 24 |
| OH_WIFI_STANDARD_11AC = 5 | 802.11ac Wi-Fi standard.<br>**Since**: 24 |
| OH_WIFI_STANDARD_11AX = 6 | 802.11ax Wi-Fi standard.<br>**Since**: 24 |
| OH_WIFI_STANDARD_11AD = 7 | 802.11ad Wi-Fi standard.<br>**Since**: 24 |


## Function description

### OH_Wifi_IsWifiEnabled()

```c
Wifi_ResultCode OH_Wifi_IsWifiEnabled(bool *enabled)
```

**Description**

Check whether the wifi switch is enabled.

**System capability**: SystemCapability.Communication.WiFi.STA

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| bool *enabled | - It is a boolean pointer used to receive wifi switch status values. Equal to true indicates that the wifi switch is turned on, false indicates that the wifi switch is turned off. The caller needs to pass in a non empty boolean pointer, otherwise an error will be returned. |

**Returns**:

| Type | Description |
| -- | -- |
| [Wifi_ResultCode](capi-oh-wifi-h.md#wifi_resultcode) | wifi functions result code.\n      For a detailed definition, please refer to [Wifi_ResultCode](capi-oh-wifi-h.md#wifi_resultcode).\n      [WIFI_SUCCESS](capi-oh-wifi-h.md#wifi_resultcode) Successfully obtained the wifi switch status.\n      [WIFI_INVALID_PARAM](capi-oh-wifi-h.md#wifi_resultcode) The input parameter enabled is a null pointer.\n      [WIFI_OPERATION_FAILED](capi-oh-wifi-h.md#wifi_resultcode) Internal execution failed.\n |

### OH_Wifi_GetDeviceMacAddress()

```c
Wifi_ResultCode OH_Wifi_GetDeviceMacAddress(char *macAddr, unsigned int *macAddrLen)
```

**Description**

Get the device Mac address.

**System capability**: SystemCapability.Communication.WiFi.STA

**Required permission**: ohos.permission.GET_WIFI_LOCAL_MAC and ohos.permission.GET_WIFI_INFO.

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| char *macAddr | - The character array of device Mac address terminated using '\0'. |
| unsigned int *macAddrLen | - The size of the memory allocated for the macAddr character array. |

**Returns**:

| Type | Description |
| -- | -- |
| [Wifi_ResultCode](capi-oh-wifi-h.md#wifi_resultcode) | wifi functions result code.      For a detailed definition, please refer to [Wifi_ResultCode](capi-oh-wifi-h.md#wifi_resultcode).      [WIFI_SUCCESS](capi-oh-wifi-h.md#wifi_resultcode) Successfully obtained the device Mac address.      [WIFI_PERMISSION_DENIED](capi-oh-wifi-h.md#wifi_resultcode) Permission denied.      [WIFI_NOT_SUPPORTED](capi-oh-wifi-h.md#wifi_resultcode) Capability not supported.      [WIFI_INVALID_PARAM](capi-oh-wifi-h.md#wifi_resultcode) The input parameter macAddr is a null pointer.      [WIFI_OPERATION_FAILED](capi-oh-wifi-h.md#wifi_resultcode) Internal execution failed.      [WIFI_STA_DISABLED](capi-oh-wifi-h.md#wifi_resultcode) Wi-Fi STA disabled. |

### OH_Wifi_GetLinkedInfo()

```c
Wifi_ResultCode OH_Wifi_GetLinkedInfo(OH_WifiLinkedInfo *info)
```

**Description**

Get wifi linked info. When macType is 1 (device MAC address), obtaining macAddress also requires the ohos.permission.GET_WIFI_LOCAL_MAC permission. This permission is available only to system apps in API versions 8–15. Starting from API 16, it is available to regular apps on PC/2-in-1 devices, while on other devices it remains restricted to system apps. If the permission is not granted, macAddress will be returned as empty. If the application has requested the ohos.permission.GET_WIFI_PEERS_MAC permission, the bssid in the returned result will be the real BSSID address; otherwise, it will be a randomized device address.

**System capability**: SystemCapability.Communication.WiFi.STA

**Required permission**: ohos.permission.GET_WIFI_INFO.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_WifiLinkedInfo](capi-wifi-oh-wifilinkedinfo.md) *info | - the data structure of the Wi-Fi connection information. |

**Returns**:

| Type | Description |
| -- | -- |
| [Wifi_ResultCode](capi-oh-wifi-h.md#wifi_resultcode) | wifi functions result code.      For a detailed definition, please refer to [Wifi_ResultCode](capi-oh-wifi-h.md#wifi_resultcode).      [WIFI_SUCCESS](capi-oh-wifi-h.md#wifi_resultcode) Successfully obtained the wifi linked info.      [WIFI_PERMISSION_DENIED](capi-oh-wifi-h.md#wifi_resultcode) Permission denied.      [WIFI_NOT_SUPPORTED](capi-oh-wifi-h.md#wifi_resultcode) Capability not supported.      [WIFI_INVALID_PARAM](capi-oh-wifi-h.md#wifi_resultcode) The input parameter info is a null pointer.      [WIFI_OPERATION_FAILED](capi-oh-wifi-h.md#wifi_resultcode) Internal execution failed. |


