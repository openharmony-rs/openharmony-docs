# oh_wifi.h

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @qq_43802146-->
<!--Designer: @qq_43802146-->
<!--Tester: @furryfurry123-->
<!--Adviser: @zhang_yixin13-->
## 概述

定义查询WIFI开关状态的接口。

**引用文件：** <ConnectivityKit/wifi/oh_wifi.h>

**库：** libwifi_ndk.so

**系统能力：** SystemCapability.Communication.WiFi.STA

**起始版本：** 13

**相关模块：** [Wifi](capi-wifi.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_WifiLinkedInfo](capi-wifi-oh-wifilinkedinfo.md) | OH_WifiLinkedInfo | 表示WIFI连接信息。此结构体描述当前STA连接的热点信息。<br> 可通过调用 [OH_Wifi_GetLinkedInfo](capi-oh-wifi-h.md#oh_wifi_getlinkedinfo) 获取这些信息。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [Wifi_ResultCode](#wifi_resultcode) | Wifi_ResultCode | 定义WIFI接口返回值的错误码。 |
| [OH_WifiLinkType](#oh_wifilinktype) | OH_WifiLinkType | 定义WIFI链路类型。 |
| [OH_WifiConnState](#oh_wificonnstate) | OH_WifiConnState | WIFI连接状态。 |
| [OH_WifiChannelWidth](#oh_wifichannelwidth) | OH_WifiChannelWidth | WIFI信道带宽。 |
| [OH_WifiCategory](#oh_wificategory) | OH_WifiCategory | WIFI类别。 |
| [OH_WifiStandard](#oh_wifistandard) | OH_WifiStandard | WIFI标准。 |

### 宏定义

| 名称 | 描述 |
| -- | -- |
| WIFI_MAX_SSID_LEN 33 | [OH_WifiLinkedInfo](capi-wifi-oh-wifilinkedinfo.md)表示ssid的最大长度，有效字符32，最后一位保留并设置为'\0'。<br>**起始版本：** 24 |
| WIFI_MAC_LEN 18 | [OH_WifiLinkedInfo](capi-wifi-oh-wifilinkedinfo.md)表示Mac地址或bssid的最大长度，有效字符长度17，最后一位为'\0'。<br>**起始版本：** 24 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [Wifi_ResultCode OH_Wifi_IsWifiEnabled(bool *enabled)](#oh_wifi_iswifienabled) | 查询WIFI开关是否开启。 |
| [Wifi_ResultCode OH_Wifi_GetDeviceMacAddress(char *macAddr, unsigned int *macAddrLen)](#oh_wifi_getdevicemacaddress) | 该接口用于获取设备真实MAC地址。 |
| [Wifi_ResultCode OH_Wifi_GetLinkedInfo(OH_WifiLinkedInfo *info)](#oh_wifi_getlinkedinfo) | 该接口用于获取WIFI连接信息。 |

## 枚举类型说明

### Wifi_ResultCode

```c
enum Wifi_ResultCode
```

**描述**

定义WIFI接口返回值的错误码。

**起始版本：** 13

| 枚举项 | 描述 |
| -- | -- |
| WIFI_SUCCESS = 0 | 操作成功。 |
| WIFI_PERMISSION_DENIED = 201 | 权限校验失败。 |
| WIFI_INVALID_PARAM = 401 | 参数错误。<br> 可能原因：1.输入参数为空指针；2.参数数值超出定义范围。 |
| WIFI_NOT_SUPPORTED = 801 | 该功能不支持。由于设备能力有限，无法调用该函数。 |
| WIFI_OPERATION_FAILED = 2501000 | 操作失败。<br> 可能原因：服务内部执行失败。 |
| WIFI_STA_DISABLED = 2501001 | STA服务未拉起。<br> 可能原因：WIFI未打开。<br>**起始版本：** 21 |

### OH_WifiLinkType

```c
enum OH_WifiLinkType
```

**描述**

定义WIFI链路类型。

**起始版本：** 24

| 枚举项 | 描述 |
| -- | -- |
| OH_WIFI_LINK_DISCONNECT = -1 | 未连接。<br>**起始版本：** 24 |
| OH_WIFI_LINK_DEFAULT_LINK = 0 | 默认链路。<br>**起始版本：** 24 |
| OH_WIFI_LINK_WIFI7_SINGLE_LINK = 1 | WIFI7单链路。<br>**起始版本：** 24 |
| OH_WIFI_LINK_WIFI7_MLSR = 2 | WIFI7 MLSR（Multi-Link Single Radio 多链路单射频）。<br>**起始版本：** 24 |
| OH_WIFI_LINK_WIFI7_EMLSR = 3 | WIFI7 EMLSR（Enhanced Multi-Link Single Radio 增强型多链路单射频）。<br>**起始版本：** 24 |
| OH_WIFI_LINK_WIFI7_STR = 4 | WIFI7 STR（Simultaneous transmit and Receive 同时发送与接收）。<br>**起始版本：** 24 |
| OH_WIFI_LINK_WIFI7_LEGACY = 5 | WIFI7传统模式。<br>**起始版本：** 24 |

### OH_WifiConnState

```c
enum OH_WifiConnState
```

**描述**

WIFI连接状态。

**起始版本：** 24

| 枚举项 | 描述 |
| -- | -- |
| OH_WIFI_CONN_SCANNING | 设备正在搜索可用的热点。<br>**起始版本：** 24 |
| OH_WIFI_CONN_CONNECTING | WIFI连接正在建立。<br>**起始版本：** 24 |
| OH_WIFI_CONN_AUTHENTICATING | WIFI连接正在进行认证。<br>**起始版本：** 24 |
| OH_WIFI_CONN_OBTAINING_IPADDR | 正在获取WIFI连接的IP地址。<br>**起始版本：** 24 |
| OH_WIFI_CONN_CONNECTED | WIFI连接已建立。<br>**起始版本：** 24 |
| OH_WIFI_CONN_DISCONNECTING | WIFI连接正在断开。<br>**起始版本：** 24 |
| OH_WIFI_CONN_DISCONNECTED | WIFI连接已断开。<br>**起始版本：** 24 |
| OH_WIFI_CONN_SPECIAL_CONNECT | WIFI连接处于特殊状态。<br>**起始版本：** 24 |
| OH_WIFI_CONN_UNKNOWN | WIFI连接建立失败。<br>**起始版本：** 24 |

### OH_WifiChannelWidth

```c
enum OH_WifiChannelWidth
```

**描述**

WIFI信道带宽。

**起始版本：** 24

| 枚举项 | 描述 |
| -- | -- |
| OH_WIFI_WIDTH_20MHZ = 0 | 20MHz信道带宽。<br>**起始版本：** 24 |
| OH_WIFI_WIDTH_40MHZ = 1 | 40MHz信道带宽。<br>**起始版本：** 24 |
| OH_WIFI_WIDTH_80MHZ = 2 | 80MHz信道带宽。<br>**起始版本：** 24 |
| OH_WIFI_WIDTH_160MHZ = 3 | 160MHz信道带宽。<br>**起始版本：** 24 |
| OH_WIFI_WIDTH_80MHZ_PLUS = 4 | 双80MHz信道带宽。<br>**起始版本：** 24 |
| OH_WIFI_WIDTH_INVALID = 5 | 无效的信道带宽。<br>**起始版本：** 24 |

### OH_WifiCategory

```c
enum OH_WifiCategory
```

**描述**

WIFI类别。

**起始版本：** 24

| 枚举项 | 描述 |
| -- | -- |
| OH_WIFI_CATEGORY_DEFAULT = 1 | 默认类别。<br>**起始版本：** 24 |
| OH_WIFI_CATEGORY_WIFI6 = 2 | WIFI6类别。<br>**起始版本：** 24 |
| OH_WIFI_CATEGORY_WIFI6_PLUS = 3 | WIFI6+类别。<br>**起始版本：** 24 |
| OH_WIFI_CATEGORY_WIFI7 = 4 | WIFI7类别。<br>**起始版本：** 24 |
| OH_WIFI_CATEGORY_WIFI7_PLUS = 5 | WIFI7+类别。<br>**起始版本：** 24 |

### OH_WifiStandard

```c
enum OH_WifiStandard
```

**描述**

WIFI标准。

**起始版本：** 24

| 枚举项 | 描述 |
| -- | -- |
| OH_WIFI_STANDARD_UNDEFINED = 0 | 无效的WIFI标准。<br>**起始版本：** 24 |
| OH_WIFI_STANDARD_11A = 1 | 802.11a WIFI标准。<br>**起始版本：** 24 |
| OH_WIFI_STANDARD_11B = 2 | 802.11b WIFI标准。<br>**起始版本：** 24 |
| OH_WIFI_STANDARD_11G = 3 | 802.11g WIFI标准。<br>**起始版本：** 24 |
| OH_WIFI_STANDARD_11N = 4 | 802.11n WIFI标准。<br>**起始版本：** 24 |
| OH_WIFI_STANDARD_11AC = 5 | 802.11ac WIFI标准。<br>**起始版本：** 24 |
| OH_WIFI_STANDARD_11AX = 6 | 802.11ax WIFI标准。<br>**起始版本：** 24 |
| OH_WIFI_STANDARD_11AD = 7 | 802.11ad WIFI标准。<br>**起始版本：** 24 |


## 函数说明

### OH_Wifi_IsWifiEnabled()

```c
Wifi_ResultCode OH_Wifi_IsWifiEnabled(bool *enabled)
```

**描述**

查询WIFI开关是否开启。

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| bool *enabled | - bool类型的指针，用于接收WIFI开关状态值。<br> 等于true表示WIFI开关开启，false表示WIFI开关关闭。<br> 需要传入非空指针，否则会返回错误。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Wifi_ResultCode](capi-oh-wifi-h.md#wifi_resultcode) | 返回操作结果，详细定义参见[Wifi_ResultCode](capi-oh-wifi-h.md#wifi_resultcode)。<br>     [WIFI_SUCCESS](capi-oh-wifi-h.md#wifi_resultcode) 查询WIFI开关状态成功。<br>     [WIFI_INVALID_PARAM](capi-oh-wifi-h.md#wifi_resultcode) 入参为空指针。<br>     [WIFI_OPERATION_FAILED](capi-oh-wifi-h.md#wifi_resultcode) 服务内部执行错误。 |

### OH_Wifi_GetDeviceMacAddress()

```c
Wifi_ResultCode OH_Wifi_GetDeviceMacAddress(char *macAddr, unsigned int *macAddrLen)
```

**描述**

该接口用于获取设备真实MAC地址。

**需要权限：** ohos.permission.GET_WIFI_LOCAL_MAC 和 ohos.permission.GET_WIFI_INFO。

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| char *macAddr | 设备MAC地址的字符数组，以'\0'结尾。 |
| unsigned int *macAddrLen | 为macAddr字符数组分配的内存大小。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Wifi_ResultCode](capi-oh-wifi-h.md#wifi_resultcode) | 返回操作结果，详细定义参见[Wifi_ResultCode](capi-oh-wifi-h.md#wifi_resultcode)。<br>     [WIFI_SUCCESS](capi-oh-wifi-h.md#wifi_resultcode) 成功获取设备MAC地址。<br>     [WIFI_PERMISSION_DENIED](capi-oh-wifi-h.md#wifi_resultcode) 权限拒绝。<br>     [WIFI_NOT_SUPPORTED](capi-oh-wifi-h.md#wifi_resultcode) 不支持该能力。<br>     [WIFI_INVALID_PARAM](capi-oh-wifi-h.md#wifi_resultcode) 输入参数macAddr是空指针。<br>     [WIFI_OPERATION_FAILED](capi-oh-wifi-h.md#wifi_resultcode) 内部执行失败。<br>     [WIFI_STA_DISABLED](capi-oh-wifi-h.md#wifi_resultcode) WIFI STA模式未启用。 |

### OH_Wifi_GetLinkedInfo()

```c
Wifi_ResultCode OH_Wifi_GetLinkedInfo(OH_WifiLinkedInfo *info)
```

**描述**

该接口用于获取WIFI连接信息。

> **说明：**
> - 当macType是1（设备MAC地址），获取macAddress还需申请ohos.permission.GET_WIFI_LOCAL_MAC权限（API version 8-15仅面向系统应用开放。从API version 16开始，在PC/2in1设备上面向普通应用开放，在其余设备上仍仅面向系统应用开放），无该权限时，macAddress返回为空。
> - 如果应用申请了ohos.permission.GET_WIFI_PEERS_MAC权限，则返回结果中的bssid为真实bssid地址，否则为随机设备地址。

**需要权限：** ohos.permission.GET_WIFI_INFO。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_WifiLinkedInfo](capi-wifi-oh-wifilinkedinfo.md) *info | - WIFI连接信息结构体。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Wifi_ResultCode](capi-oh-wifi-h.md#wifi_resultcode) | 返回操作结果，详细定义参见[Wifi_ResultCode](capi-oh-wifi-h.md#wifi_resultcode)。<br>     [WIFI_SUCCESS](capi-oh-wifi-h.md#wifi_resultcode) 成功获取WIFI连接信息。<br>     [WIFI_PERMISSION_DENIED](capi-oh-wifi-h.md#wifi_resultcode) 权限拒绝。<br>     [WIFI_NOT_SUPPORTED](capi-oh-wifi-h.md#wifi_resultcode) 不支持该能力。<br>     [WIFI_INVALID_PARAM](capi-oh-wifi-h.md#wifi_resultcode) 输入参数info是空指针。<br>     [WIFI_OPERATION_FAILED](capi-oh-wifi-h.md#wifi_resultcode) 内部执行失败。<br>     [WIFI_STA_DISABLED](capi-oh-wifi-h.md#wifi_resultcode) WIFI STA模式未启用。 |


