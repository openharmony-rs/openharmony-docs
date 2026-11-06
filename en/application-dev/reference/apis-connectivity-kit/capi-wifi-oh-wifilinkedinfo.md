# OH_WifiLinkedInfo

<!--Kit: Connectivity Kit--> 
<!--Subsystem: Communication--> 
<!--Owner: @qq_43802146--> 
<!--Designer: @qq_43802146--> 
<!--Tester: @furryfurry123--> 
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=8f1c4b5bf09fe9c480702fce5e0972d8873c6b23 translatedAt=2026-09-09T09:01:43.618Z pushedAt=2026-09-09T11:24:47.152Z -->

```c
typedef struct {...} OH_WifiLinkedInfo
```

## Overview

Describes the Wi-Fi connection information. This struct describes the hotspot information of the connected STA.<br> The information can be obtained by calling [OH_Wifi_GetLinkedInfo](capi-oh-wifi-h.md#oh_wifi_getlinkedinfo).

**Since**: 24

**Related module**: [Wifi](capi-wifi.md)

**Header file:** [oh_wifi.h](capi-oh-wifi-h.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| char ssid[WIFI_MAX_SSID_LEN] | Service set identifier (SSID), which is used to obtain the public name of the Wi-Fi hotspot to which the current device is connected (that is, the name of the wireless network). The encoding format is UTF-8.<br>**WIFI_MAX_SSID_LEN** is set to **33**, indicating the length.|
| int32_t rssi | Received signal strength indicator (RSSI), in dBm.|
| int32_t band | Wi-Fi band information of the hotspot. **1** indicates 2.4 GHz, and **2** indicates 5 GHz.|
| int32_t linkSpeed | Uplink speed of the Wi-Fi access point, in Mbit/s.|
| int32_t rxLinkSpeed | Downlink speed of the Wi-Fi access point, in Mbit/s.|
| int32_t maxSupportedTxLinkSpeed | Maximum uplink speed supported, in Mbit/s.|
| int32_t maxSupportedRxLinkSpeed | Maximum downlink speed supported, in Mbit/s.|
| int32_t frequency | Frequency of the hotspot, in MHz.|
| bool isHidden | Whether the Wi-Fi access point is hidden. The value **true** indicates that the Wi-Fi access point is hidden; the value **false** indicates the opposite. |
| bool isRestricted | Whether data volume is restricted at the Wi-Fi access point. The value **true** indicates that data volume is restricted, and the value **false** indicates the opposite. |
| int32_t macType | MAC address type. **0** indicates a random MAC address, and **1** indicates the device MAC address.|
| char macAddress[WIFI_MAC_LEN] | MAC address of the device. When **macType** is **1**, the **ohos.permission.GET_WIFI_LOCAL_MAC** permission is required.<br>Format: **AA:BB:CC:DD:EE:FF**<br>Length: **WIFI_MAC_LEN** is set to **18**.|
| uint32_t ipAddress | IP address of the connected network.|
| [OH_WifiConnState](capi-oh-wifi-h.md#oh_wificonnstate) connState | Wi-Fi connection state. For details, see [OH_WifiConnState](capi-oh-wifi-h.md#oh_wificonnstate).|
| [OH_WifiChannelWidth](capi-oh-wifi-h.md#oh_wifichannelwidth) channelWidth | Channel bandwidth of the current hotspot. For details, see [OH_WifiChannelWidth](capi-oh-wifi-h.md#oh_wifichannelwidth).|
| [OH_WifiStandard](capi-oh-wifi-h.md#oh_wifistandard) wifiStandard | Wi-Fi standard of the currently connected hotspot. For details, see [OH_WifiStandard](capi-oh-wifi-h.md#oh_wifistandard).|
| [OH_WifiCategory](capi-oh-wifi-h.md#oh_wificategory) supportedWifiCategory | Highest Wi-Fi category supported by the hotspot. For details, see [OH_WifiCategory](capi-oh-wifi-h.md#oh_wificategory).|
| bool isHiLinkNetwork | Whether the hotspot supports HiLink. The value **true** indicates that it is supported, and **false** indicates that it is not supported.|
| [OH_WifiLinkType](capi-oh-wifi-h.md#oh_wifilinktype) wifiLinkType | Wi-Fi link type. For details, see [OH_WifiLinkType](capi-oh-wifi-h.md#oh_wifilinktype).|

