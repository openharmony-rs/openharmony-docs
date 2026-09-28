# log.h

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @suxunquan-->
<!--Designer: @milkbread123-->
<!--Tester: @yufeifei-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=d279d307cd9e8aff378b718e4c6eab1a3f2598f8 translatedAt=2026-09-21T02:38:15.725Z pushedAt=2026-09-22T01:29:30.398Z -->

## Overview

Defines the log APIs of the HiLog module, through which log printing related functions are implemented. When outputting logs, a user first defines the business domain to which the logs belong and the log TAG, then selects the corresponding API based on the type and level, and specifies the parameter privacy identifier to output the log content.<br> Business domain: specifies the business domain to which the specified log corresponds. It is user-defined and used to identify the subsystem and module of a service. It is a hexadecimal base integer ranging from 0x0 to 0xFFFF. If it is out of range, the log cannot be printed.<br> Log TAG: a string constant used to identify the class or service where the call is located.<br> Log level: DEBUG, INFO, WARN, ERROR, and FATAL.<br> Parameter format: a printf-like `%` format, including a format string (including parameter type identifiers) and variable arguments.<br> Privacy parameter identifier: add {public} or {private} after the `%` symbol and before the type in each parameter of the format string. Note: if no privacy identifier is specified for a parameter, the parameter is private by default.

**File to include**: <hilog/log.h>

**Library**: libhilog_ndk.z.so

**System capability**: SystemCapability.HiviewDFX.HiLog

**Since**: 8

**Related module**: [HiLog](capi-hilog.md)

## Summary

### Enum

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [LogType](#logtype) | LogType | Enumerates the log types. You can use this enum to specify the type of output logs. Currently, only **LOG_APP** is available.<br>|
| [LogLevel](#loglevel) | LogLevel | Enumerates the log levels. This enum is used to define log levels. Recommended usage of each level: <br> DEBUG: Used to record process details more detailed than the INFO level. Logs at this level help analyze business processes and locate problems in more detail. DEBUG logs are not printed by default in official release versions; they are printed only in debug versions or when the debug switch is enabled. <br> INFO: Used to record key business process nodes to reproduce the main running process of a business; records abnormal information that is expected (such as no network signal, login failure, etc.). These logs should be recorded by the dominant module in the business to avoid duplicate recording in multiple called modules or low-level functions. <br> WARN: A relatively serious unexpected situation occurs, but it has little impact on users, and the program can recover automatically or through simple operations. <br> ERROR: An error occurs in the program or function, which affects the normal running of the function or normal use by users. It can be recovered but at a high cost, such as resetting data. <br> FATAL: A major fatal exception, indicating that the program or function is about to crash and the fault cannot be recovered. <br> |
| [PreferStrategy](#preferstrategy) | PreferStrategy | Enumerates the preference strategies. This enum is used in [OH_LOG_SetLogLevel](#oh_log_setloglevel). The minimum log level that takes effect varies according to the strategy.|

### Macros

| Name| Description|
| -- | -- |
| OH_LOG_DEBUG(type, ...) ((void)OH_LOG_Print((type), LOG_DEBUG, LOG_DOMAIN, LOG_TAG, \_\_VA_ARGS__)) | Indicates DEBUG logs. This is a function-like macro. Before using this macro, define **LOG_DOMAIN** and **LOG_TAG** at the beginning of the source file.<br>**Since**: 8|
| OH_LOG_INFO(type, ...) ((void)OH_LOG_Print((type), LOG_INFO, LOG_DOMAIN, LOG_TAG, \_\_VA_ARGS__)) | Indicates INFO logs. This is a function-like macro. Before using this macro, define **LOG_DOMAIN** and **LOG_TAG** at the beginning of the source file.<br>**Since**: 8|
| OH_LOG_WARN(type, ...) ((void)OH_LOG_Print((type), LOG_WARN, LOG_DOMAIN, LOG_TAG, \_\_VA_ARGS__)) | Indicates WARN logs. This is a function-like macro. Before using this macro, define **LOG_DOMAIN** and **LOG_TAG** at the beginning of the source file.<br>**Since**: 8|
| OH_LOG_ERROR(type, ...) ((void)OH_LOG_Print((type), LOG_ERROR, LOG_DOMAIN, LOG_TAG, \_\_VA_ARGS__)) | Indicates ERROR logs. This is a function-like macro. Before using this macro, define **LOG_DOMAIN** and **LOG_TAG** at the beginning of the source file.<br>**Since**: 8|
| OH_LOG_FATAL(type, ...) ((void)OH_LOG_Print((type), LOG_FATAL, LOG_DOMAIN, LOG_TAG, \_\_VA_ARGS__)) | Indicates FATAL logs. This is a function-like macro. Before using this macro, define **LOG_DOMAIN** and **LOG_TAG** at the beginning of the source file.<br><br>**Since**: 8|
|LOG_DOMAIN| Specifies the service domain of the output log. The default value is **0**. The value range is 0x0 to 0xFFFF. If the value of **domainID** exceeds the range, the log cannot be printed.<br>**Since**: 8|
|LOG_TAG | Identifies the class or service behavior where the log is called. The value is a string constant, which is **NULL** by default. The maximum length is 31 bytes. If the length exceeds 31 bytes, the log will be truncated. The value must be a non-null string. Otherwise, the log cannot be printed. Chinese characters are not recommended, because they may cause garbled characters or alignment issues.<br>**Since**: 8|

### Functions

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [int OH_LOG_Print(LogType type, LogLevel level, unsigned int domain, const char *tag, const char *fmt, ...)](#oh_log_print) | - |  Outputs logs of the specified **type**, **level**, **domain**, **tag**, and variables determined by the format specifier and privacy identifier in the printf format.|
| [int OH_LOG_PrintMsg(LogType type, LogLevel level, unsigned int domain, const char *tag, const char *message)](#oh_log_printmsg) | - |  Outputs constant log strings of the specified **type**, **level**, **domain**, and **tag**.|
| [int OH_LOG_PrintMsgByLen(LogType type, LogLevel level, unsigned int domain, const char *tag, size_t tagLen, const char *message, size_t messageLen)](#oh_log_printmsgbylen) | - |  Outputs log constant strings of the specified **domain**, **tag**, and **level**. The tag and string length must be specified. Unlike **OH_LOG_PrintMsg**, this API allows strings without terminators.|
| [int OH_LOG_VPrint(LogType type, LogLevel level, unsigned int domain, const char *tag, const char *fmt, va_list ap)](#oh_log_vprint) | - |  Outputs logs of the specified **type**, **level**, **domain**, **tag**, and variables determined by the format specifier and privacy identifier in the printf format. The variables are of the **va_list** type.|
| [bool OH_LOG_IsLoggable(unsigned int domain, const char *tag, LogLevel level)](#oh_log_isloggable) | - | Checks whether logs of the specified service domain, tag, and level can be printed.|
| [typedef void (\*LogCallback)(const LogType type, const LogLevel level, const unsigned int domain, const char *tag, const char *msg)](#logcallback) | LogCallback | Customizes the processing of HiLog logs in the callback.|
| [void OH_LOG_SetCallback(LogCallback callback)](#oh_log_setcallback) | - | Registers a callback function. After this function is called, the custom callback can receive all HiLog logs of the current process.<br> Note that whether this API is called or not, it does not change the default log processing of the current process.|
| [void OH_LOG_SetMinLogLevel(LogLevel level)](#oh_log_setminloglevel) | - | Sets the minimum log level.|
| [void OH_LOG_SetLogLevel(LogLevel level, PreferStrategy prefer)](#oh_log_setloglevel) | - | Sets the minimum log level of the current application process. You can configure different preference strategies.|

> **NOTE**
>
> If the set log level is lower than the [global log level](../../dfx/hilog.md#displaying-and-setting-log-levels), the **OH_LOG_SetMinLogLevel()** setting does not take effect.
>
> In the debug applications, the **OH_LOG_SetMinLogLevel()** and **OH_LOG_SetLogLevel()** functions do not take effect.

## Enum Description

### LogType

```c
enum LogType
```

**Description**

Enumerates the log types. You can use this function to specify the type of output logs. Currently, only **LOG_APP** is available.<br>

**Since**: 8

| Enum Item| Description|
| -- | -- |
| LOG_APP = 0 | Application log.|

### LogLevel

```c
enum LogLevel
```

**Description**

Enumerates the log levels. This enum is used to define log levels. Recommended usage of each level: <br> DEBUG: Used to record process details more detailed than the INFO level. Logs at this level help analyze business processes and locate problems in more detail. DEBUG logs are not printed by default in official release versions; they are printed only in debug versions or when the debug switch is enabled. <br> INFO: Used to record key business process nodes to reproduce the main running process of a business; records abnormal information that is expected (such as no network signal, login failure, etc.). These logs should be recorded by the dominant module in the business to avoid duplicate recording in multiple called modules or low-level functions. <br> WARN: A relatively serious unexpected situation occurs, but it has little impact on users, and the program can recover automatically or through simple operations. <br> ERROR: An error occurs in the program or function, which affects the normal running of the function or normal use by users. It can be recovered but at a high cost, such as resetting data. <br> FATAL: A major fatal exception, indicating that the program or function is about to crash and the fault cannot be recovered. <br>

**Since**: 8

| Enum Item| Description|
| -- | -- |
| LOG_DEBUG = 3 | DEBUG level to be used by **OH_LOG_DEBUG**.|
| LOG_INFO = 4 | INFO level to be used by **OH_LOG_INFO**.|
| LOG_WARN = 5 | WARN level to be used by **OH_LOG_WARN**.|
| LOG_ERROR = 6 | ERROR level to be used by **OH_LOG_ERROR**.|
| LOG_FATAL = 7 | FATAL level to be used by **OH_LOG_FATAL**.|

### PreferStrategy

```c
enum PreferStrategy
```

**Description**

Enumerates the preference strategies. This enum is used in [OH_LOG_SetLogLevel](#oh_log_setloglevel). The minimum log level that takes effect varies according to the strategy.

**Since**: 21

| Enum Item| Description|
| -- | -- |
| UNSET_LOGLEVEL = 0 | Clears the setting. The minimum log level that actually takes effect is the minimum level controlled by the system. |
| PREFER_CLOSE_LOG = 1 | The minimum log level that actually takes effect is the larger value of the new log level and the system-controlled minimum log level.|
| PREFER_OPEN_LOG = 2 | The minimum log level that actually takes effect is the smaller value of the new log level and the system-controlled minimum log level.|

## Function Description

For detailed usage of each interface, see [Using HiLog (C/C++)](../../dfx/hilog-guidelines-ndk.md).

### OH_LOG_Print()

```c
int OH_LOG_Print(LogType type, LogLevel level, unsigned int domain, const char *tag, const char *fmt, ...)
```

**Description**

Outputs logs of the specified **type**, **level**, **domain**, **tag**, and variables determined by the format specifier and privacy identifier in the printf format.

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [LogType](capi-log-h.md#logtype) type | Log type. The type for third-party applications is defined by **LOG_APP**.|
| [LogLevel](capi-log-h.md#loglevel) level | Log level. The value can be **LOG_DEBUG**, **LOG_INFO**, **LOG_WARN**, **LOG_ERROR**, and **LOG_FATAL**.|
| unsigned int domain | Service domain. Its value is a hexadecimal integer ranging from 0x0 to 0xFFFF. If the value exceeds the range, logs cannot be printed.|
| const char *tag | Log tag, which is a string used to identify the class, file, or service. A tag can contain a maximum of 31 bytes. If a tag exceeds this limit, it will be truncated. Chinese characters are not recommended because garbled characters or alignment problems may occur.|
| const char *fmt | Format string, which is an enhancement of a printf format string and supports the privacy identifier. Specifically, **{public}** or **{private}** is added between the `%` character and the format specifier in each parameter. |
| ... | Parameter list corresponding to the parameter type in the format string. The number and type of parameters must be mapped onto the identifier in the format string.|

**Returns**

| Type| Description|
| -- | -- |
| int | **0** or a larger value if the operation is successful; a value smaller than **0** otherwise.<br> Possible failure causes: The **LogLevel** passed in is lower than the allowed log level; the **domain** is out of range; the **tag** is a null pointer; the CPU is overloaded; the memory is insufficient; the number of logs on the device is too large.|

### OH_LOG_PrintMsg()

```c
int OH_LOG_PrintMsg(LogType type, LogLevel level, unsigned int domain, const char *tag, const char *message)
```

**Description**

Outputs constant log strings of the specified **type**, **level**, **domain**, and **tag**.

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [LogType](capi-log-h.md#logtype) type | Log type. The type for third-party applications is defined by **LOG_APP**.|
| [LogLevel](capi-log-h.md#loglevel) level | Log level. The value can be **LOG_DEBUG**, **LOG_INFO**, **LOG_WARN**, **LOG_ERROR**, and **LOG_FATAL**.|
| unsigned int domain | Service domain. Its value is a hexadecimal integer ranging from 0x0 to 0xFFFF. If the value exceeds the range, logs cannot be printed.|
| const char *tag | Log tag, which is a string used to identify the class, file, or service. A tag can contain a maximum of 31 bytes. If a tag exceeds this limit, it will be truncated. Chinese characters are not recommended because garbled characters or alignment problems may occur.|
| const char *message | Constant log string.|

**Returns**

| Type| Description|
| -- | -- |
| int | **0** or a larger value if the operation is successful; a value smaller than **0** otherwise.<br> Possible failure causes: The **LogLevel** passed in is lower than the allowed log level; the **domain** is out of range; the **tag** is a null pointer; the CPU is overloaded; the memory is insufficient; the number of logs on the device is too large.|

### OH_LOG_PrintMsgByLen()

```c
int OH_LOG_PrintMsgByLen(LogType type, LogLevel level, unsigned int domain, const char *tag, size_t tagLen, const char *message, size_t messageLen)
```

**Description**

Outputs log constant strings of the specified **domain**, **tag**, and **level**. The tag and string length must be specified. Unlike **OH_LOG_PrintMsg**, this API allows strings without terminators.

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [LogType](capi-log-h.md#logtype) type | Log type. The type for third-party applications is defined by **LOG_APP**.|
| [LogLevel](capi-log-h.md#loglevel) level | Log level. The value can be **LOG_DEBUG**, **LOG_INFO**, **LOG_WARN**, **LOG_ERROR**, and **LOG_FATAL**.|
| unsigned int domain | Service domain. Its value is a hexadecimal integer ranging from 0x0 to 0xFFFF. If the value exceeds the range, logs cannot be printed.|
| const char *tag | Log tag, which is a string used to identify the class, file, or service. A tag can contain a maximum of 31 bytes. If a tag exceeds this limit, it will be truncated. Chinese characters are not recommended because garbled characters or alignment problems may occur.|
| size_t tagLen | Length of the tag.|
| const char *message | Constant log string.|
| size_t messageLen | Length of the constant string, which is less than 3500 characters.|

**Returns**

| Type| Description|
| -- | -- |
| int | **0** or a larger value if the operation is successful; a value smaller than **0** otherwise.<br> Possible failure causes: The **LogLevel** passed in is lower than the allowed log level; the **domain** is out of range; the **tag** is a null pointer; the CPU is overloaded; the memory is insufficient; the number of logs on the device is too large.|

### OH_LOG_VPrint()

```c
int OH_LOG_VPrint(LogType type, LogLevel level, unsigned int domain, const char *tag, const char *fmt, va_list ap)
```

**Description**

Outputs logs of the specified **type**, **level**, **domain**, **tag**, and variables determined by the format specifier and privacy identifier in the printf format. The variables are of the **va_list** type.

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [LogType](capi-log-h.md#logtype) type | Log type. The type for third-party applications is defined by **LOG_APP**.|
| [LogLevel](capi-log-h.md#loglevel) level | Log level. The value can be **LOG_DEBUG**, **LOG_INFO**, **LOG_WARN**, **LOG_ERROR**, and **LOG_FATAL**.|
| unsigned int domain | Service domain. Its value is a hexadecimal integer ranging from 0x0 to 0xFFFF. If the value exceeds the range, logs cannot be printed.|
| const char *tag | Log tag, which is a string used to identify the class, file, or service. A tag can contain a maximum of 31 bytes. If a tag exceeds this limit, it will be truncated. Chinese characters are not recommended because garbled characters or alignment problems may occur.|
| const char *fmt | Format string, which is an enhancement of a printf format string and supports the privacy identifier. Specifically, **{public}** or **{private}** is added between the `%` character and the format specifier in each parameter. |
| va_list ap | Parameter list of the **va_list** type that corresponds to the parameter type in the format string. The number and type of parameters must be mapped onto the identifier in the format string.|

**Returns**

| Type| Description|
| -- | -- |
| int | **0** or a larger value if the operation is successful; a value smaller than **0** otherwise.<br> Possible failure causes: The **LogLevel** passed in is lower than the allowed log level; the **domain** is out of range; the **tag** is a null pointer; the CPU is overloaded; the memory is insufficient; the number of logs on the device is too large.|

### OH_LOG_IsLoggable()

```c
bool OH_LOG_IsLoggable(unsigned int domain, const char *tag, LogLevel level)
```

**Description**

Checks whether logs of the specified service domain, tag, and level can be printed.

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| unsigned int domain | Service domain. Its value is a hexadecimal integer ranging from 0x0 to 0xFFFF. If the value exceeds the range, logs cannot be printed.|
| const char *tag | Log tag, which is a string used to identify the class, file, or service. A tag can contain a maximum of 31 bytes. If a tag exceeds this limit, it will be truncated. Chinese characters are not recommended because garbled characters or alignment problems may occur.|
| [LogLevel](capi-log-h.md#loglevel) level | Log level. The value can be **LOG_DEBUG**, **LOG_INFO**, **LOG_WARN**, **LOG_ERROR**, and **LOG_FATAL**.|

**Returns**

| Type| Description|
| -- | -- |
| bool | **true** if the specified logs can be output; **false** otherwise.|

### OH_LOG_DEBUG()

```c
OH_LOG_DEBUG(type, ...)((void)OH_LOG_Print((type), LOG_DEBUG, LOG_DOMAIN, LOG_TAG, __VA_ARGS__))
```

**Description**

Indicates DEBUG logs. This is a function-like macro. Before using this macro, define **LOG_DOMAIN** and **LOG_TAG** at the beginning of the source file.<br>

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| type | Log type. The third-party application log type is [LOG_APP](capi-log-h.md#logtype).|
| fmt | Format string, which is an enhancement of a printf format string and supports the privacy identifier. Specifically, **{public}** or **{private}** is added between the `%` character and the format specifier in each parameter. |
| ... | Parameter list corresponding to the parameter type in the format string. The number and type of parameters must be mapped onto the identifier in the format string.|

**See also**

[OH_LOG_Print](capi-log-h.md#oh_log_print)


### OH_LOG_INFO()

```c
OH_LOG_INFO(type, ...)((void)OH_LOG_Print((type), LOG_INFO, LOG_DOMAIN, LOG_TAG, __VA_ARGS__))
```

**Description**

Indicates INFO logs. This is a function-like macro. Before using this macro, define **LOG_DOMAIN** and **LOG_TAG** at the beginning of the source file.<br>

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| type | Log type. The type for third-party applications is defined by **LOG_APP**.|
| fmt | Format string, which is an enhancement of a printf format string and supports the privacy identifier. Specifically, **{public}** or **{private}** is added between the `%` character and the format specifier in each parameter. |
| ... | Parameter list corresponding to the parameter type in the format string. The number and type of parameters must be mapped onto the identifier in the format string.|

**See also**

[OH_LOG_Print](capi-log-h.md#oh_log_print)


### OH_LOG_WARN()

```c
OH_LOG_WARN(type, ...)((void)OH_LOG_Print((type), LOG_WARN, LOG_DOMAIN, LOG_TAG, __VA_ARGS__))
```

**Description**

Indicates WARN logs. This is a function-like macro. Before using this macro, define **LOG_DOMAIN** and **LOG_TAG** at the beginning of the source file.

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| type | Log type. The third-party application log type is [LOG_APP](capi-log-h.md#logtype).|
| fmt | Format string, which is an enhancement of a printf format string and supports the privacy identifier. Specifically, {public} or {private} is added between the `%` character and the format specifier in each parameter. |
| ... | Parameter list corresponding to the parameter type in the format string. The number and type of parameters must be mapped onto the identifier in the format string.|

**See also**

[OH_LOG_Print](capi-log-h.md#oh_log_print)


### OH_LOG_ERROR()

```c
OH_LOG_ERROR(type, ...)((void)OH_LOG_Print((type), LOG_ERROR, LOG_DOMAIN, LOG_TAG, __VA_ARGS__))
```

**Description**

Indicates ERROR logs. This is a function-like macro. Before using this macro, define **LOG_DOMAIN** and **LOG_TAG** at the beginning of the source file.

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| type | Log type. The third-party application log type is [LOG_APP](capi-log-h.md#logtype).|
| fmt | Format string, which is an enhancement of a printf format string and supports the privacy identifier. Specifically, **{public}** or **{private}** is added between the `%` character and the format specifier in each parameter. |
| ... | Parameter list corresponding to the parameter type in the format string. The number and type of parameters must be mapped onto the identifier in the format string.|

**See also**

[OH_LOG_Print](capi-log-h.md#oh_log_print)


### OH_LOG_FATAL()

```c
OH_LOG_FATAL(type, ...)((void)OH_LOG_Print((type), LOG_FATAL, LOG_DOMAIN, LOG_TAG, __VA_ARGS__))
```

**Description**

Indicates FATAL logs. This is a function-like macro. Before using this macro, define **LOG_DOMAIN** and **LOG_TAG** at the beginning of the source file.<br>

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| type | Log type. The third-party application log type is [LOG_APP](capi-log-h.md#logtype).|
| fmt | Format string, which is an enhancement of a printf format string and supports the privacy identifier. Specifically, **{public}** or **{private}** is added between the `%` character and the format specifier in each parameter. |
| ... | Parameter list corresponding to the parameter type in the format string. The number and type of parameters must be mapped onto the identifier in the format string.|

**See also**

[OH_LOG_Print](capi-log-h.md#oh_log_print)


### LogCallback()

```c
typedef void (*LogCallback)(const LogType type, const LogLevel level, const unsigned int domain, const char *tag, const char *msg)
```

**Description**

Customizes the processing of HiLog logs in the callback.

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [const LogType](capi-log-h.md#logtype) type | Log type. The third-party application log type is [LOG_APP](capi-log-h.md#logtype).|
| [ const LogLevel](capi-log-h.md#loglevel) level | Log level. The value can be **LOG_DEBUG**, **LOG_INFO**, **LOG_WARN**, **LOG_ERROR**, and **LOG_FATAL**.|
|  const unsigned int domain | Service domain. Its value is a hexadecimal integer ranging from 0x0 to 0xFFFF. If the value exceeds the range, logs cannot be printed.|
|  const char \*tag | Log tag, which is a string used to identify the class, file, or service. A tag can contain a maximum of 31 bytes. If a tag exceeds this limit, it will be truncated. Chinese characters are not recommended because garbled characters or alignment problems may occur.|
| const char \*msg | Log content, which is made up of formatted log strings.|

### OH_LOG_SetCallback()

```c
void OH_LOG_SetCallback(LogCallback callback)
```

**Description**

Registers a callback function. After this function is called, the custom callback can receive all HiLog logs of the current process.<br> Note that whether this API is called or not, it does not change the default log processing of the current process.

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [LogCallback](capi-log-h.md#logcallback) callback | Custom callback function. If processing of logs is not needed, a null pointer can be transferred.|

### OH_LOG_SetMinLogLevel()

```c
void OH_LOG_SetMinLogLevel(LogLevel level)
```

**Description**

Sets the minimum log level.

**NOTE**

1. If the set log level is lower than the [global log level](../../dfx/hilog.md#displaying-and-setting-log-levels), the setting does not take effect.

2. This function does not take effect for debug applications.

**Since**: 15

**Parameters**

| Name| Description|
| -- | -- |
| [LogLevel](capi-log-h.md#loglevel) level | Log level.|

### OH_LOG_SetLogLevel()

```c
void OH_LOG_SetLogLevel(LogLevel level, PreferStrategy prefer)
```

**Description**

Sets the minimum log level of the current application process.

You can configure different preference strategies using the **prefer** parameter. The **PREFER_CLOSE_LOG** strategy has the same effect as the **OH_LOG_SetMinLogLevel()** function.

Note: This function does not take effect for debug applications.

**Since**: 21

**Parameters**

| Name| Description|
| -- | -- |
| [LogLevel](capi-log-h.md#loglevel) level | Log level.|
| [PreferStrategy](capi-log-h.md#preferstrategy) prefer | Preference strategy.|