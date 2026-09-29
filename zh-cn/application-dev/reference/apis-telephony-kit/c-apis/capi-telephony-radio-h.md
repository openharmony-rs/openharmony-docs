# telephony_radio.h

## 概述

Provides C interface for the telephony radio.

**引用文件：** <telephony/core_service/telephony_radio_type.h>

**库：** libtelephony_radio.so

**起始版本：** 13

**相关模块：** [](capi-.md)

## 汇总

### 函数

| 名称 | 描述 |
| -- | -- |
| [Telephony_RadioResult OH_Telephony_GetNetworkState(Telephony_NetworkState *state)](#oh_telephony_getnetworkstate) | 获取网络状态。 |

## 函数说明

### OH_Telephony_GetNetworkState()

```c
Telephony_RadioResult OH_Telephony_GetNetworkState(Telephony_NetworkState *state)
```

**描述：**

获取网络状态。

**需要权限：** ohos.permission.GET_NETWORK_INFO

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [Telephony_NetworkState](capi--telephony-networkstate.md) *state | 用户接收网络状态信息的结构体。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [Telephony_RadioResult](capi-telephony-radio-type-h.md#telephony_radioresult) | 结果定义在 [Telephony_RadioResult](capi-telephony-radio-type-h.md#telephony_radioresult)。<br>[TEL_RADIO_SUCCESS](capi-telephony-radio-type-h.md#telephony_radioresult) 成功。<br>[TEL_RADIO_PERMISSION_DENIED](capi-telephony-radio-type-h.md#telephony_radioresult) 权限错误。<br>[TEL_RADIO_ERR_MARSHALLING_FAILED](capi-telephony-radio-type-h.md#telephony_radioresult) 编组错误。<br>[TEL_RADIO_ERR_SERVICE_CONNECTION_FAILED](capi-telephony-radio-type-h.md#telephony_radioresult) 连接电话服务错误。<br>[TEL_RADIO_ERR_OPERATION_FAILED](capi-telephony-radio-type-h.md#telephony_radioresult) 操作电话服务错误。<br>[TEL_RADIO_ERR_INVALID_PARAM](capi-telephony-radio-type-h.md#telephony_radioresult) 参数错误。 |


