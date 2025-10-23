# oh_location.h
<!--Kit: Location Kit-->
<!--Subsystem: Location-->
<!--Owner: @liu-binjun-->
<!--Designer: @liu-binjun-->
<!--Tester: @mhy123456789-->
<!--Adviser: @RayShih-->

## 概述

定义查询位置开关状态、启动定位、停止定位的接口。

**引用文件：** <LocationKit/oh_location.h>

**库：** liblocation_ndk.so

**系统能力：** SystemCapability.Location.Location.Core

**起始版本：** 13

**相关模块：** [Location](capi-location.md)

## 汇总

### 函数

| 名称 | 描述 |
| -- | -- |
| [Location_ResultCode OH_Location_IsLocatingEnabled(bool* enabled)](#oh_location_islocatingenabled) | 查询位置开关是否开启。 |
| [Location_ResultCode OH_Location_StartLocating(const Location_RequestConfig* requestConfig)](#oh_location_startlocating) | 启动定位并订阅位置变化。 |
| [Location_ResultCode OH_Location_StopLocating(const Location_RequestConfig* requestConfig)](#oh_location_stoplocating) | 停止定位并取消订阅位置变化。 |

## 函数说明

### OH_Location_IsLocatingEnabled()

```
Location_ResultCode OH_Location_IsLocatingEnabled(bool* enabled)
```

**描述**

查询位置开关是否开启。

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| bool* enabled | bool类型的指针，用于接收位置开关状态值。<br> 等于true表示位置开关开启，false表示位置开关关闭。<br> 需要传入非空指针，否则会返回错误。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Location_ResultCode](capi-oh-location-type-h.md#location_resultcode) | 返回操作结果，详细定义参见[Location_ResultCode](capi-oh-location-type-h.md#location_resultcode)。<br>     [LOCATION_SUCCESS](capi-oh-location-type-h.md#location_resultcode) 查询位置开关状态成功。<br>     [LOCATION_INVALID_PARAM](capi-oh-location-type-h.md#location_resultcode) 入参是空指针。<br>     [LOCATION_SERVICE_UNAVAILABLE](capi-oh-location-type-h.md#location_resultcode) 位置服务运行异常导致查询位置开关状态失败。 |

### OH_Location_StartLocating()

```
Location_ResultCode OH_Location_StartLocating(const Location_RequestConfig* requestConfig)
```

**描述**

启动定位并订阅位置变化。

**需要权限：** ohos.permission.APPROXIMATELY_LOCATION

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const Location_RequestConfig](capi-location-location-requestconfig.md)* requestConfig | 指向定位请求参数的指针，该参数用于指定发起定位的场景信息和位置上报间隔。<br> 详细定义请参考[Location_RequestConfig](capi-location-location-requestconfig.md)，可以使用[OH_Location_CreateRequestConfig](capi-oh-location-type-h.md#oh_location_createrequestconfig)创建。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Location_ResultCode](capi-oh-location-type-h.md#location_resultcode) | 返回操作结果，详细定义参见[Location_ResultCode](capi-oh-location-type-h.md#location_resultcode)。<br>     [LOCATION_SUCCESS](capi-oh-location-type-h.md#location_resultcode) 启动定位成功。<br>     [LOCATION_INVALID_PARAM](capi-oh-location-type-h.md#location_resultcode) 入参requestConfig为空指针。<br>     [LOCATION_PERMISSION_DENIED](capi-oh-location-type-h.md#location_resultcode) 权限校验失败。<br>     [LOCATION_NOT_SUPPORTED](capi-oh-location-type-h.md#location_resultcode) 当前设备不支持该功能。<br>     [LOCATION_SERVICE_UNAVAILABLE](capi-oh-location-type-h.md#location_resultcode) 位置服务运行异常。<br>     [LOCATION_SWITCH_OFF](capi-oh-location-type-h.md#location_resultcode) 位置开关未打开导致无法启动定位。 |

### OH_Location_StopLocating()

```
Location_ResultCode OH_Location_StopLocating(const Location_RequestConfig* requestConfig)
```

**描述**

停止定位并取消订阅位置变化。

**需要权限：** ohos.permission.APPROXIMATELY_LOCATION

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const Location_RequestConfig](capi-location-location-requestconfig.md)* requestConfig | 指向定位请求参数的指针。<br> 该参数需要与[OH_Location_StartLocating](capi-oh-location-h.md#oh_location_startlocating)中的requestConfig是同一个指针。<br> 详细定义请参考[Location_RequestConfig](capi-location-location-requestconfig.md)。<br> 需要传入非空指针，否则会返回错误。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [Location_ResultCode](capi-oh-location-type-h.md#location_resultcode) | 返回操作结果，详细定义参见[Location_ResultCode](capi-oh-location-type-h.md#location_resultcode)。<br>     [LOCATION_SUCCESS](capi-oh-location-type-h.md#location_resultcode) 停止定位成功。<br>     [LOCATION_INVALID_PARAM](capi-oh-location-type-h.md#location_resultcode) 1. 入参为空指针。<br>         2. 入参与[OH_Location_StartLocating](capi-oh-location-h.md#oh_location_startlocating)的requestConfig指针不同。<br>     [LOCATION_PERMISSION_DENIED](capi-oh-location-type-h.md#location_resultcode) 权限校验失败。<br>     [LOCATION_NOT_SUPPORTED](capi-oh-location-type-h.md#location_resultcode) 当前设备不支持该功能。<br>     [LOCATION_SERVICE_UNAVAILABLE](capi-oh-location-type-h.md#location_resultcode) 位置服务运行异常。<br>     [LOCATION_SWITCH_OFF](capi-oh-location-type-h.md#location_resultcode) 位置开关未打开。 |


