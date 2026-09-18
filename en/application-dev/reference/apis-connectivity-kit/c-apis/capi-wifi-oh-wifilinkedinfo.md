# OH_WifiLinkedInfo

```c
typedef struct OH_WifiLinkedInfo {...} OH_WifiLinkedInfo
```

## Overview

Represents the Wi-Fi connection information.<br> This structure describes the hotspot information of the current station connection. The information can be obtained by calling [OH_Wifi_GetLinkedInfo](capi-oh-wifi-h.md#oh_wifi_getlinkedinfo).

**Since**: 24

**Related module**: [Wifi](capi-wifi.md)

**Header file**: [oh_wifi.h](capi-oh-wifi-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| char ssid[WIFI_MAX_SSID_LEN] | Service set identifier (SSID).<br> For the length, see {@link WIFI_MAX_SSID_LEN}.<br>**Since**: 24 |
| char bssid[WIFI_MAC_LEN] | Basic service set identifier (BSSID). If the application has requested the ohos.permission.GET_WIFI_PEERS_MAC permission, the bssid . in the returned result will be the real BSSID address; otherwise, it will be a randomized device address. format: "AA:BB:CC:DD:EE:FF" For the length, see {@link WIFI_MAC_LEN}.<br>**Since**: 24 |
| int32_t rssi | Received signal strength indicator (RSSI).<br>**Since**: 24 |
| int32_t band | Wi-Fi band information of the hotspot. 1 indicates 2.4GHZ; 2 indicates 5GHZ<br>**Since**: 24 |
| int32_t linkSpeed | Wi-Fi link speed, in Mbps.<br>**Since**: 24 |
| int32_t rxLinkSpeed | Downlink speed, in Mbps.<br>**Since**: 24 |
| int32_t maxSupportedTxLinkSpeed | Maximum supported TX link speed, in Mbps.<br>**Since**: 24 |
| int32_t maxSupportedRxLinkSpeed | Maximum supported RX link speed, in Mbps.<br>**Since**: 24 |
| int32_t frequency | Wi-Fi frequency of the hotspot, in MHz.<br>**Since**: 24 |
| bool isHidden | Indicates whether the SSID is hidden.<br>**Since**: 24 |
| bool isRestricted | Indicates whether data access is restricted.<br>**Since**: 24 |
| int32_t macType | MAC address type. 0 indicates random MAC address; 1 indicates device MAC address<br>**Since**: 24 |
| char macAddress[WIFI_MAC_LEN] | MAC address of the device. When macType is 1 require ohos.permission.GET_WIFI_LOCAL_MAC permission format: "AA:BB:CC:DD:EE:FF" For the maximum length, see {@link WIFI_MAC_LEN}.<br>**Since**: 24 |
| uint32_t ipAddress | IP address of the connected network.<br>**Since**: 24 |
| [OH_WifiConnState](capi-oh-wifi-h.md#oh_wificonnstate) connState | Wi-Fi connection state. For details, see [OH_WifiConnState](capi-oh-wifi-h.md#oh_wificonnstate).<br>**Since**: 24 |
| [OH_WifiChannelWidth](capi-oh-wifi-h.md#oh_wifichannelwidth) channelWidth | Current AP channel width. For details, see [OH_WifiChannelWidth](capi-oh-wifi-h.md#oh_wifichannelwidth).<br>**Since**: 24 |
| [OH_WifiStandard](capi-oh-wifi-h.md#oh_wifistandard) wifiStandard | Wi-Fi standard. For details, see [OH_WifiStandard](capi-oh-wifi-h.md#oh_wifistandard).<br>**Since**: 24 |
| [OH_WifiCategory](capi-oh-wifi-h.md#oh_wificategory) supportedWifiCategory | Supported Wi-Fi category. For details, see [OH_WifiCategory](capi-oh-wifi-h.md#oh_wificategory).<br>**Since**: 24 |
| bool isHiLinkNetwork | Indicates whether the network is a HiLink network.<br>**Since**: 24 |
| [OH_WifiLinkType](capi-oh-wifi-h.md#oh_wifilinktype) wifiLinkType | Wi-Fi link type. For details, see [OH_WifiLinkType](capi-oh-wifi-h.md#oh_wifilinktype).<br>**Since**: 24 |


