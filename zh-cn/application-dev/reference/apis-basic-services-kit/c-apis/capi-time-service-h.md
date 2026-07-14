# time_service.h

## 概述

Declares the APIs for obtaining the time zone information.

**库：** libtime_service_ndk.so

**系统能力：** SystemCapability.MiscServices.Time

**起始版本：** 12

**相关模块：** [TimeService](capi-timeservice.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [TimeService_ErrCode](#timeservice_errcode) | TimeService_ErrCode | 枚举错误码。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [TimeService_ErrCode OH_TimeService_GetTimeZone(char *timeZone, uint32_t len)](#oh_timeservice_gettimezone) | 获取当前系统时区。 |

## 枚举类型说明

### TimeService_ErrCode

```c
enum TimeService_ErrCode
```

**描述**

枚举错误码。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| TIMESERVICE_ERR_OK = 0 | 成功。 |
| TIMESERVICE_ERR_INTERNAL_ERROR = 13000001 | 获取系统参数失败。 |
| TIMESERVICE_ERR_INVALID_PARAMETER = 13000002 | 无效的参数。 |


## 函数说明

### OH_TimeService_GetTimeZone()

```c
TimeService_ErrCode OH_TimeService_GetTimeZone(char *timeZone, uint32_t len)
```

**描述**

获取当前系统时区。

**系统能力：** SystemCapability.MiscServices.Time

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| char *timeZone | 用于写入一个时区ID字符串的缓冲区，成功时写入当前系统时区ID字符串，失败时写入空字符串，字符串以'\0'结尾。 |
| uint32_t len | 参数timeZone所指向缓冲区的容量，单位为字节，包含结束字符'\0'。当前时区字符串没有最大长度规格，建议分配至少31字节。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [TimeService_ErrCode](capi-time-service-h.md#timeservice_errcode) | 返回`TIMESERVICE_ERR_OK`表示成功。<br>     <br>返回`TIMESERVICE_ERR_INTERNAL_ERROR`表示获取系统参数失败。<br>     <br>返回`TIMESERVICE_ERR_INVALID_PARAMETER`表示timeZone为NULL指针或时区名称（不包括结束字符（'\0'））的大小大于或等于len。 |


