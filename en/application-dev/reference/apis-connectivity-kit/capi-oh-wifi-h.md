# oh_wifi.h

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @qq_43802146-->
<!--Designer: @qq_43802146-->
<!--Tester: @furryfurry123-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=b5e5ebda6b4c13f35bbaf4ad555abce6585e4cdc translatedAt=2026-09-09T09:03:01.073Z pushedAt=2026-09-09T10:57:09.708Z -->

## Overview

Defines APIs for querying the Wi-Fi status, obtaining the device MAC address, and obtaining the Wi-Fi connection information.

**File to include**: <ConnectivityKit/wifi/oh_wifi.h>

**Library**: libwifi_ndk.so

**System capability**: SystemCapability.Communication.WiFi.STA

**Since**: 13

**Related module**: [Wifi](capi-wifi.md)

## Summary

### Structs

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [OH_WifiLinkedInfo](capi-wifi-oh-wifilinkedinfo.md) | OH_WifiLinkedInfo | Describes the Wi-Fi connection information. This struct describes the hotspot information of the connected STA.<br> The information can be obtained by calling [OH_Wifi_GetLinkedInfo](capi-oh-wifi-h.md#oh_wifi_getlinkedinfo). |

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [Wifi_ResultCode](#wifi_resultcode) | Wifi_ResultCode | Enumerates the error codes returned by Wi-Fi APIs. |
| [OH_WifiLinkType](#oh_wifilinktype) | OH_WifiLinkType | Enumerates the Wi-Fi link types. |
| [OH_WifiConnState](#oh_wificonnstate) | OH_WifiConnState | Enumerates the Wi-Fi connection statuses. |
| [OH_WifiChannelWidth](#oh_wifichannelwidth) | OH_WifiChannelWidth | Enumerates the Wi-Fi channel bandwidths. |
| [OH_WifiCategory](#oh_wificategory) | OH_WifiCategory | Enumerates the Wi-Fi categories. |
| [OH_WifiStandard](#oh_wifistandard) | OH_WifiStandard | Enumerates the Wi-Fi standards. |

### Macros

| Name| Description|
| -- | -- |
| WIFI_MAX_SSID_LEN 33 | [OH_WifiLinkedInfo](capi-wifi-oh-wifilinkedinfo.md) indicates the maximum length of the SSID. The value contains a maximum of 32 characters, and the last bit is reserved and set to '\0'.<br>**Since:** 24|
| WIFI_MAC_LEN 18 | [OH_WifiLinkedInfo](capi-wifi-oh-wifilinkedinfo.md) indicates the maximum length of the MAC address or BSSID. The value contains a maximum of 17 characters, and the last bit is '\0'.<br>**Since:** 24|

### Functions

| Name| Description|
| -- | -- |
| [Wifi_ResultCode OH_Wifi_IsWifiEnabled(bool *enabled)](#oh_wifi_iswifienabled) | Checks whether Wi-Fi is enabled. |
| [Wifi_ResultCode OH_Wifi_GetDeviceMacAddress(char *macAddr, unsigned int *macAddrLen)](#oh_wifi_getdevicemacaddress) | Obtains the actual MAC address of a device.|
| [Wifi_ResultCode OH_Wifi_GetLinkedInfo(OH_WifiLinkedInfo *info)](#oh_wifi_getlinkedinfo) | Obtains Wi-Fi connection information. |

## Enum Description

### Wifi_ResultCode

```c
enum Wifi_ResultCode
```

**Description**

Enumerates the error codes returned by Wi-Fi APIs.

**Since**: 13

| Enum Item| Description|
| -- | -- |
| WIFI_SUCCESS = 0 | The operation is successful.|
| WIFI_PERMISSION_DENIED = 201 | Permission verification fails.|
| WIFI_INVALID_PARAM = 401 | Invalid parameter.<br> Possible causes: 1. The input parameter is a null pointer. 2. The value is out of the range.|
| WIFI_NOT_SUPPORTED = 801 | Function not supported due to limited device capabilities.|
| WIFI_OPERATION_FAILED = 2501000 | Operation failed.<br> Possible causes: The internal execution of the service fails.|
| WIFI_STA_DISABLED = 2501001 | The STA service fails to be started.<br> Possible causes: Wi-Fi is not enabled.<br>**Since:** 21 |

### OH_WifiLinkType

```c
enum OH_WifiLinkType
```

**Description**

Enumerates the Wi-Fi link types.

**Since**: 24

| Enum Item| Description|
| -------- | -------- |
| OH_WIFI_LINK_DISCONNECT = -1 | Disconnected. |
| OH_WIFI_LINK_DEFAULT_LINK = 0 | Default link. |
| OH_WIFI_LINK_WIFI7_SINGLE_LINK = 1 | Wi-Fi 7 single link. |
| OH_WIFI_LINK_WIFI7_MLSR = 2 | Wi-Fi 7 multi-link single-radio (MLSR). |
| OH_WIFI_LINK_WIFI7_EMLSR = 3 | Wi-Fi 7 enhanced multi-link single-radio (EMLSR). |
| OH_WIFI_LINK_WIFI7_STR = 4 | Wi-Fi 7 simultaneous transmit and receive (STR). |
| OH_WIFI_LINK_WIFI7_LEGACY = 5 | Wi-Fi 7 legacy mode. |

### OH_WifiConnState

```c
enum OH_WifiConnState
```

**Description**

Enumerates the Wi-Fi connection statuses.

**Since**: 24

| Enum Item| Description|
| -------- | -------- |
| OH_WIFI_CONN_SCANNING | The device is searching for available hotspots. |
| OH_WIFI_CONN_CONNECTING | The Wi-Fi connection is being established. |
| OH_WIFI_CONN_AUTHENTICATING | The Wi-Fi connection is being authenticated. |
| OH_WIFI_CONN_OBTAINING_IPADDR | The IP address of the Wi-Fi connection is being obtained.|
| OH_WIFI_CONN_CONNECTED | The Wi-Fi connection is established.|
| OH_WIFI_CONN_DISCONNECTING | The Wi-Fi connection is being disconnected.|
| OH_WIFI_CONN_DISCONNECTED | The Wi-Fi connection is disconnected.|
| OH_WIFI_CONN_SPECIAL_CONNECT | The Wi-Fi connection is in a special state. |
| OH_WIFI_CONN_UNKNOWN | The Wi-Fi connection fails to be established.|

### OH_WifiChannelWidth

```c
enum OH_WifiChannelWidth
```

**Description**

Enumerates the Wi-Fi channel bandwidths.

**Since**: 24

| Enum Item| Description|
| -------- | -------- |
| OH_WIFI_WIDTH_20MHZ = 0 | 20 MHz channel bandwidth. |
| OH_WIFI_WIDTH_40MHZ = 1 | 40 MHz channel bandwidth. |
| OH_WIFI_WIDTH_80MHZ = 2 | 80 MHz channel bandwidth. |
| OH_WIFI_WIDTH_160MHZ = 3 | 160 MHz channel bandwidth. |
| OH_WIFI_WIDTH_80MHZ_PLUS = 4 | 80 MHz channel bandwidth for two channels. |
| OH_WIFI_WIDTH_INVALID = 5 | Invalid channel bandwidth. |

### OH_WifiCategory

```c
enum OH_WifiCategory
```

**Description**

Enumerates the Wi-Fi categories.

**Since**: 24

|Enum Item| Description|
| -------- | -------- |
| OH_WIFI_CATEGORY_DEFAULT = 1 | Default category.|
| OH_WIFI_CATEGORY_WIFI6 = 2 | Wi-Fi 6. |
| OH_WIFI_CATEGORY_WIFI6_PLUS = 3 | Wi-Fi 6+. |
| OH_WIFI_CATEGORY_WIFI7 = 4 | Wi-Fi 7. |
| OH_WIFI_CATEGORY_WIFI7_PLUS = 5 | Wi-Fi 7+. |

### OH_WifiStandard

```c
enum OH_WifiStandard
```

**Description**

Enumerates the Wi-Fi standards.

**Since**: 24

| Enum Item| Description|
| -------- | -------- |
| OH_WIFI_STANDARD_UNDEFINED = 0 | Invalid Wi-Fi standard. |
| OH_WIFI_STANDARD_11A = 1 | 802.11a. |
| OH_WIFI_STANDARD_11B = 2 | 802.11b. |
| OH_WIFI_STANDARD_11G = 3 | 802.11g. |
| OH_WIFI_STANDARD_11N = 4 | 802.11n. |
| OH_WIFI_STANDARD_11AC = 5 | 802.11ac. |
| OH_WIFI_STANDARD_11AX = 6 | 802.11ax. |
| OH_WIFI_STANDARD_11AD = 7 | 802.11ad. |


## Function Description

### OH_Wifi_IsWifiEnabled()

```c
Wifi_ResultCode OH_Wifi_IsWifiEnabled(bool *enabled)
```

**Description**

Checks whether Wi-Fi is enabled.

**Since**: 13

**Parameters**

| Name| Description|
| -- | -- |
| bool *enabled | Pointer to the boolean value indicating the Wi-Fi state.<br> The value **true** indicates that Wi-Fi is enabled, and **false** indicates the opposite.<br> A non-null pointer must be passed in; otherwise, an error is returned. |

**Returns**

| Type| Description|
| -- | -- |
| [Wifi_ResultCode](capi-oh-wifi-h.md#wifi_resultcode) | Operation result. For details, see [Wifi_ResultCode](capi-oh-wifi-h.md#wifi_resultcode).<br> [WIFI_SUCCESS](capi-oh-wifi-h.md#wifi_resultcode): The Wi-Fi status is obtained successfully.<br> [WIFI_INVALID_PARAM](capi-oh-wifi-h.md#wifi_resultcode): The input parameter is a null pointer.<br> [WIFI_OPERATION_FAILED](capi-oh-wifi-h.md#wifi_resultcode): An internal error occurs during service execution. |

### OH_Wifi_GetDeviceMacAddress()

```c
Wifi_ResultCode OH_Wifi_GetDeviceMacAddress(char *macAddr, unsigned int *macAddrLen)
```

**Description**

Obtains the actual MAC address of a device.

**Required permissions**: ohos.permission.GET_WIFI_LOCAL_MAC and ohos.permission.GET_WIFI_INFO

**Since**: 21

**Parameters**

| Name| Description|
| -- | -- |
| char *macAddr | Character array of the device MAC address, which ends with **\0**.|
| unsigned int *macAddrLen | Memory size allocated to **macAddr**.|

**Returns**

| Type| Description|
| -- | -- |
| [Wifi_ResultCode](capi-oh-wifi-h.md#wifi_resultcode) | Operation result. For details, see [Wifi_ResultCode](capi-oh-wifi-h.md#wifi_resultcode).<br> [WIFI_SUCCESS](capi-oh-wifi-h.md#wifi_resultcode): The MAC address of the device is obtained successfully.<br> [WIFI_PERMISSION_DENIED](capi-oh-wifi-h.md#wifi_resultcode): The permission is denied.<br> [WIFI_NOT_SUPPORTED](capi-oh-wifi-h.md#wifi_resultcode): This capability is not supported.<br> [WIFI_INVALID_PARAM](capi-oh-wifi-h.md#wifi_resultcode): The input **macAddr** is a null pointer.<br> [WIFI_OPERATION_FAILED](capi-oh-wifi-h.md#wifi_resultcode): An internal error occurs during service execution.<br> [WIFI_STA_DISABLED](capi-oh-wifi-h.md#wifi_resultcode): The Wi-Fi STA mode is disabled. |

### OH_Wifi_GetLinkedInfo()

```c
Wifi_ResultCode OH_Wifi_GetLinkedInfo(OH_WifiLinkedInfo *info)
```

**Description**

Obtains Wi-Fi connection information.

> **NOTE**
> - If **macType** is set to **1** (device MAC address), you also need to apply for the ohos.permission.GET_WIFI_LOCAL_MAC permission to obtain the value of **macAddress**. (For API version 8 to 15, this permission is available only to system applications. For API version 16 and later, this permission is available to common applications on PCs/2-in-1 devices, and is available only to system applications on other devices.) If the ohos.permission.GET_WIFI_LOCAL_MAC permission is not granted, no value is returned for **macAddress**.
> - If the application has the ohos.permission.GET_WIFI_PEERS_MAC permission, **bssid** in the return value is a real BSSID; otherwise, **bssid** is a random device address.

**Required permissions**: ohos.permission.GET_WIFI_INFO

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_WifiLinkedInfo](capi-wifi-oh-wifilinkedinfo.md) *info | Pointer to the Wi-Fi connection information struct. |

**Returns**

| Type| Description|
| -- | -- |
| [Wifi_ResultCode](capi-oh-wifi-h.md#wifi_resultcode) | Operation result. For details, see [Wifi_ResultCode](capi-oh-wifi-h.md#wifi_resultcode).<br> [WIFI_SUCCESS](capi-oh-wifi-h.md#wifi_resultcode): The Wi-Fi connection information is obtained successfully.<br> [WIFI_PERMISSION_DENIED](capi-oh-wifi-h.md#wifi_resultcode): The permission is denied.<br> [WIFI_NOT_SUPPORTED](capi-oh-wifi-h.md#wifi_resultcode): The capability is not supported.<br> [WIFI_INVALID_PARAM](capi-oh-wifi-h.md#wifi_resultcode): The input **info** is a null pointer.<br> [WIFI_OPERATION_FAILED](capi-oh-wifi-h.md#wifi_resultcode): An internal error occurs during service execution.<br> [WIFI_STA_DISABLED](capi-oh-wifi-h.md#wifi_resultcode): The Wi-Fi STA mode is not enabled. |


