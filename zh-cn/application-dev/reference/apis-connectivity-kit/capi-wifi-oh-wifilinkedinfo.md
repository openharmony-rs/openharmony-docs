# OH_WifiLinkedInfo

<!--Kit: Connectivity Kit--> 
<!--Subsystem: Communication--> 
<!--Owner: @qq_43802146--> 
<!--Designer: @qq_43802146--> 
<!--Tester: @furryfurry123--> 
<!--Adviser: @zhang_yixin13-->
```c
typedef struct {...} OH_WifiLinkedInfo
```

## 概述

表示WIFI连接信息。此结构体描述当前STA连接的热点信息。<br> 可通过调用 [OH_Wifi_GetLinkedInfo](capi-oh-wifi-h.md#oh_wifi_getlinkedinfo) 获取这些信息。

**起始版本：** 24

**相关模块：** [Wifi](capi-wifi.md)

**所在头文件：** [oh_wifi.h](capi-oh-wifi-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| char ssid[WIFI_MAX_SSID_LEN] | 服务集标识符（ssid）用于获取当前设备已连接的WIFI热点的公开名称（即无线网络的名称），编码格式为UTF-8。<br>长度 WIFI_MAX_SSID_LEN = 18。<br>**起始版本：** 24 |
| int32_t rssi | 热点的信号强度(dBm)。RSSI（Received Signal Strength Indicator，接收信号强度指示）。<br>**起始版本：** 24 |
| int32_t band | 热点的WIFI频段信息。1表示2.4GHz；2表示5GHz。<br>**起始版本：** 24 |
| int32_t linkSpeed |  WLAN接入点的上行速度单位Mbps。<br>**起始版本：** 24 |
| int32_t rxLinkSpeed | WLAN接入点的下行速度单位Mbps。<br>**起始版本：** 24 |
| int32_t maxSupportedTxLinkSpeed | 当前支持的最大上行速率单位Mbps。<br>**起始版本：** 24 |
| int32_t maxSupportedRxLinkSpeed | 当前支持的最大下行速率单位Mbps。<br>**起始版本：** 24 |
| int32_t frequency | 热点的WIFI频率，单位：MHz。<br>**起始版本：** 24 |
| bool isHidden | WLAN接入点是否是隐藏网络，true表示是隐藏网络，false表示不是隐藏网络。<br>**起始版本：** 24 |
| bool isRestricted | WLAN接入点是否限制数据量，true表示限制，false表示不限制。<br>**起始版本：** 24 |
| int32_t macType | MAC地址类型。0 - 随机MAC地址，1 - 设备MAC地址。<br>**起始版本：** 24 |
| char macAddress[WIFI_MAC_LEN] | 设备的MAC地址。当macType为1时需要申请ohos.permission.GET_WIFI_LOCAL_MAC权限。<br>格式："AA:BB:CC:DD:EE:FF"<br>长度 WIFI_MAC_LEN = 18。<br>**起始版本：** 24 |
| uint32_t ipAddress | 已连接网络的IP地址。<br>**起始版本：** 24 |
| [OH_WifiConnState](capi-oh-wifi-h.md#oh_wificonnstate) connState | WIFI连接状态。详情参见 [OH_WifiConnState](capi-oh-wifi-h.md#oh_wificonnstate)。<br>**起始版本：** 24 |
| [OH_WifiChannelWidth](capi-oh-wifi-h.md#oh_wifichannelwidth) channelWidth | 当前热点的信道带宽。详情参见 [OH_WifiChannelWidth](capi-oh-wifi-h.md#oh_wifichannelwidth)。<br>**起始版本：** 24 |
| [OH_WifiStandard](capi-oh-wifi-h.md#oh_wifistandard) wifiStandard | 当前连接热点的WIFI标准。详情参见 [OH_WifiStandard](capi-oh-wifi-h.md#oh_wifistandard)。<br>**起始版本：** 24 |
| [OH_WifiCategory](capi-oh-wifi-h.md#oh_wificategory) supportedWifiCategory | 热点支持的最高WIFI级别。详情参见 [OH_WifiCategory](capi-oh-wifi-h.md#oh_wificategory)。<br>**起始版本：** 24 |
| bool isHiLinkNetwork | 热点是否支持hilink，true表示支持，false表示不支持。<br>**起始版本：** 24 |
| [OH_WifiLinkType](capi-oh-wifi-h.md#oh_wifilinktype) wifiLinkType | WIFI链路类型。详情参见 [OH_WifiLinkType](capi-oh-wifi-h.md#oh_wifilinktype)。<br>**起始版本：** 24 |

