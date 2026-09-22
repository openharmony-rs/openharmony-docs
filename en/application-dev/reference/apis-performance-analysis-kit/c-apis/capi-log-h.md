# log.h

## Overview

Defines the logging functions of the HiLog module.<br> Before outputting logs, you must define the service domain, and log tag, use the function with the specified log type and level, and specify the privacy identifier. <ul><li>Service domain: used to identify the subsystem and module of a service. Its value is a hexadecimal integer ranging from 0x0 to 0xFFFF.  <li>Log tag: a string used to identify the class, file, or service.</li>  <li>Log level: <b>DEBUG</b>, <b>INFO</b>, <b>WARN</b>, <b>ERROR</b>, and <b>FATAL</b></li>  <li>Parameter format: a printf format string that starts with a % character, including format specifiers and variable parameters.</li>  <li>Privacy identifier: {public} or {private} added between the % character and the format specifier in<br>each parameter. Note that each parameter has a privacy identifier. If no privacy identifier is added,<br>the parameter is considered to be <b>private</b>.</li></ul> <br>Sample code:<br>Defining the service domain and log tag:<br>    #include <hilog/log.h><br>    #define LOG_DOMAIN 0x0201<br>    #define LOG_TAG "MY_TAG"<br>Outputting logs:<br>    HILOG_WARN([LOG_APP](capi-log-h.md#logtype), "Failed to visit %{private}s, reason:%{public}d.", url, errno); Output result: 05-06 15:01:06.870 1051 1051 W 0201/MY_TAG: Failed to visit <private>, reason:503.

**Include**: <hilog/log.h>

**Library**: libhilog_ndk.z.so

**System capability**: SystemCapability.HiviewDFX.HiLog

**Since**: 8

**Related module**: [HiLog](capi-hilog.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [LogType](#logtype) | LogType | Enumerates log types.<br> Currently, <b>LOG_APP</b> is available. |
| [LogLevel](#loglevel) | LogLevel | Enumerates log levels.<br> You are advised to select log levels based on their respective usage scenarios: <ul><li><b>DEBUG</b>: used for debugging and disabled from commercial releases</li> <li><b>INFO</b>: used for logging important system running status and steps in key processes</li> <li><b>WARN</b>: used for logging unexpected exceptions that have little impact on user experience and can automatically recover. Logs at this level are generally output when such exceptions are detected and captured.</li> <li><b>ERROR</b>: used for logging malfunction that affects user experience and cannot automatically recover</li> <li><b>FATAL</b>: used for logging major exceptions that have severely affected user experience and should not occur.</li></ul> |
| [PreferStrategy](#preferstrategy) | PreferStrategy | Enumerates preference strategy to be used in [OH_LOG_SetLogLevel](capi-log-h.md#oh_log_setloglevel).<br> You are advised to select preference strategy based on their respective usage scenarios. |

### Macro

| Name | Description |
| -- | -- |
| LOG_DOMAIN 0 | Defines the service domain for a log file.<br> The service domain is used to identify the subsystem and module of a service. Its value is a hexadecimal integer ranging from 0x0 to 0xFFFF. If the value is beyond the range, its significant bits are automatically truncated.<br>**Since**: 8 |
| LOG_TAG NULL | Defines a string constant used to identify the class, file, or service.<br>**Since**: 8 |
| OH_LOG_DEBUG(type, ...) ((void)OH_LOG_Print((type), LOG_DEBUG, LOG_DOMAIN, LOG_TAG, \_\_VA_ARGS\_\_)) | Outputs debug logs. This is a function-like macro.<br> Before calling this function, define the log service domain and log tag. Generally, you need to define them at the beginning of the source file.<br>**Since**: 8 |
| OH_LOG_INFO(type, ...) ((void)OH_LOG_Print((type), LOG_INFO, LOG_DOMAIN, LOG_TAG, \_\_VA_ARGS\_\_)) | Outputs informational logs. This is a function-like macro.<br> Before calling this function, define the log service domain and log tag. Generally, you need to define them at the beginning of the source file.<br>**Since**: 8 |
| OH_LOG_WARN(type, ...) ((void)OH_LOG_Print((type), LOG_WARN, LOG_DOMAIN, LOG_TAG, \_\_VA_ARGS\_\_)) | Outputs warning logs. This is a function-like macro.<br> Before calling this function, define the log service domain and log tag. Generally, you need to define them at the beginning of the source file.<br>**Since**: 8 |
| OH_LOG_ERROR(type, ...) ((void)OH_LOG_Print((type), LOG_ERROR, LOG_DOMAIN, LOG_TAG, \_\_VA_ARGS\_\_)) | Outputs error logs. This is a function-like macro.<br> Before calling this function, define the log service domain and log tag. Generally, you need to define them at the beginning of the source file.<br>**Since**: 8 |
| OH_LOG_FATAL(type, ...) ((void)OH_LOG_Print((type), LOG_FATAL, LOG_DOMAIN, LOG_TAG, \_\_VA_ARGS\_\_)) | Outputs fatal logs. This is a function-like macro.<br> Before calling this function, define the log service domain and log tag. Generally, you need to define them at the beginning of the source file.<br>**Since**: 8 |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [int OH_LOG_Print(LogType type, LogLevel level, unsigned int domain, const char *tag, const char *fmt, ...)](#oh_log_print) | - | Outputs logs.<br> You can use this function to output logs based on the specified log type, log level, service domain, log tag, and variable parameters determined by the format specifier and privacy identifier in the printf format. |
| [int OH_LOG_PrintMsg(LogType type, LogLevel level, unsigned int domain, const char *tag, const char *message)](#oh_log_printmsg) | - | Outputs logs.<br> You can use this function to output logs based on the specified log type, log level, service domain, log tag, and message text. |
| [int OH_LOG_PrintMsgByLen(LogType type, LogLevel level, unsigned int domain, const char *tag, size_t tagLen, const char *message, size_t messageLen)](#oh_log_printmsgbylen) | - | Outputs logs.<br> You can use this function to output logs based on the specified log type, log level, service domain, log tag, message text and message length. |
| [int OH_LOG_VPrint(LogType type, LogLevel level, unsigned int domain, const char *tag, const char *fmt, va_list ap)](#oh_log_vprint) | - | Outputs logs.<br> You can use this function to output logs based on the specified log type, log level, service domain, log tag, and a va_list instead of variable parameters determined by the format specifier and privacy identifier in the printf format. |
| [bool OH_LOG_IsLoggable(unsigned int domain, const char *tag, LogLevel level)](#oh_log_isloggable) | - | Checks whether logs of the specified service domain, log tag, and log level can be output. |
| [typedef void (\*LogCallback)(const LogType type, const LogLevel level, const unsigned int domain, const char *tag, const char *msg)](#logcallback) | LogCallback | Defines the function pointer type for the user-defined log processing function. |
| [void OH_LOG_SetCallback(LogCallback callback)](#oh_log_setcallback) | - | Set the user-defined log processing function.<br> After calling this function, the callback function implemented by the user can receive all hilogs of the current process. Note that it will not change the default behavior of hilog logs of the current process, no matter whether this interface is called or not. |
| [void OH_LOG_SetMinLogLevel(LogLevel level)](#oh_log_setminloglevel) | - | Sets the lowest log level of the current application process. |
| [void OH_LOG_SetLogLevel(LogLevel level, PreferStrategy prefer)](#oh_log_setloglevel) | - | Sets the lowest log level of the current application process. Different preference strategy can be set. |

### Variable

| Name | Description |
| -- | -- |
| void (*LogCallback)(const LogType type, const LogLevel level, const unsigned int domain, const char *tag, const char *msg) | Defines the function pointer type for the user-defined log processing function.<br>**Since**: 11 |

## Enum type description

### LogType

```c
enum LogType
```

**Description**

Enumerates log types.<br> Currently, <b>LOG_APP</b> is available.

**System capability**: SystemCapability.HiviewDFX.HiLog

**Since**: 8

| Enum item | Description |
| -- | -- |
| LOG_APP = 0 | Third-party application logs |

### LogLevel

```c
enum LogLevel
```

**Description**

Enumerates log levels.<br> You are advised to select log levels based on their respective usage scenarios: <ul><li><b>DEBUG</b>: used for debugging and disabled from commercial releases</li> <li><b>INFO</b>: used for logging important system running status and steps in key processes</li> <li><b>WARN</b>: used for logging unexpected exceptions that have little impact on user experience and can automatically recover. Logs at this level are generally output when such exceptions are detected and captured.</li> <li><b>ERROR</b>: used for logging malfunction that affects user experience and cannot automatically recover</li> <li><b>FATAL</b>: used for logging major exceptions that have severely affected user experience and should not occur.</li></ul>

**System capability**: SystemCapability.HiviewDFX.HiLog

**Since**: 8

| Enum item | Description |
| -- | -- |
| LOG_DEBUG = 3 | Debug level to be used by [OH_LOG_DEBUG](capi-log-h.md#宏定义) |
| LOG_INFO = 4 | Informational level to be used by [OH_LOG_INFO](capi-log-h.md#宏定义) |
| LOG_WARN = 5 | Warning level to be used by [OH_LOG_WARN](capi-log-h.md#宏定义) |
| LOG_ERROR = 6 | Error level to be used by [OH_LOG_ERROR](capi-log-h.md#宏定义) |
| LOG_FATAL = 7 | Fatal level to be used by [OH_LOG_FATAL](capi-log-h.md#宏定义) |

### PreferStrategy

```c
enum PreferStrategy
```

**Description**

Enumerates preference strategy to be used in [OH_LOG_SetLogLevel](capi-log-h.md#oh_log_setloglevel).<br> You are advised to select preference strategy based on their respective usage scenarios.

**System capability**: SystemCapability.HiviewDFX.HiLog

**Since**: 21

| Enum item | Description |
| -- | -- |
| UNSET_LOGLEVEL = 0 | Used to unset SetLogLevel, then none is set |
| PREFER_CLOSE_LOG = 1 | The actual lowest log level is determined by the maximum level between the new level and the system-controlled level. This is equivalent to calling OH_LOG_SetMinLogLevel. |
| PREFER_OPEN_LOG = 2 | The actual lowest log level is determined by the minimum level between the new level and the system-controlled level. |


## Function description

### OH_LOG_Print()

```c
int OH_LOG_Print(LogType type, LogLevel level, unsigned int domain, const char *tag, const char *fmt, ...)
```

**Description**

Outputs logs.<br> You can use this function to output logs based on the specified log type, log level, service domain, log tag, and variable parameters determined by the format specifier and privacy identifier in the printf format.

**System capability**: SystemCapability.HiviewDFX.HiLog

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| [LogType](capi-log-h.md#logtype) type | Indicates the log type. The type for third-party applications is defined by [LOG_APP](capi-log-h.md#logtype). |
| [LogLevel](capi-log-h.md#loglevel) level | Indicates the log level, which can be <b>LOG_DEBUG</b>, <b>LOG_INFO</b>, <b>LOG_WARN</b>, <b>LOG_ERROR</b>, and <b>LOG_FATAL</b>. |
| unsigned int domain | Indicates the service domain of logs. Its value is a hexadecimal integer ranging from 0x0 to 0xFFFF. |
| const char *tag | Indicates the log tag, which is a string used to identify the class, file, or service behavior. |
| const char *fmt | Indicates the format string, which is an enhancement of a printf format string and supports the privacy identifier. Specifically, {public} or {private} is added between the % character and the format specifier in each parameter. |
| [](capi-log-h.md#).[](capi-log-h.md#).[](capi-log-h.md#).[](capi-log-h.md#) | Indicates a list of parameters. The number and type of parameters must map onto the format specifiers in the format string. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns <b>0</b> or a larger value if the operation is successful; returns a value smaller  than <b>0</b> otherwise. |

### OH_LOG_PrintMsg()

```c
int OH_LOG_PrintMsg(LogType type, LogLevel level, unsigned int domain, const char *tag, const char *message)
```

**Description**

Outputs logs.<br> You can use this function to output logs based on the specified log type, log level, service domain, log tag, and message text.

**System capability**: SystemCapability.HiviewDFX.HiLog

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [LogType](capi-log-h.md#logtype) type | Indicates the log type. The type for third-party applications is defined by [LOG_APP](capi-log-h.md#logtype). |
| [LogLevel](capi-log-h.md#loglevel) level | Indicates the log level, which can be <b>LOG_DEBUG</b>, <b>LOG_INFO</b>, <b>LOG_WARN</b>, <b>LOG_ERROR</b>, and <b>LOG_FATAL</b>. |
| unsigned int domain | Indicates the service domain of logs. Its value is a hexadecimal integer ranging from 0x0 to 0xFFFF. |
| const char *tag | Indicates the log tag, which is a string used to identify the class, file, or service behavior. |
| const char *message | Indicates the log string. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns <b>0</b> or a larger value if the operation is successful; returns a value smaller  than <b>0</b> otherwise. |

### OH_LOG_PrintMsgByLen()

```c
int OH_LOG_PrintMsgByLen(LogType type, LogLevel level, unsigned int domain, const char *tag, size_t tagLen, const char *message, size_t messageLen)
```

**Description**

Outputs logs.<br> You can use this function to output logs based on the specified log type, log level, service domain, log tag, message text and message length.

**System capability**: SystemCapability.HiviewDFX.HiLog

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [LogType](capi-log-h.md#logtype) type | Indicates the log type. The type for third-party applications is defined by [LOG_APP](capi-log-h.md#logtype). |
| [LogLevel](capi-log-h.md#loglevel) level | Indicates the log level, which can be <b>LOG_DEBUG</b>, <b>LOG_INFO</b>, <b>LOG_WARN</b>, <b>LOG_ERROR</b>, and <b>LOG_FATAL</b>. |
| unsigned int domain | Indicates the service domain of logs. Its value is a hexadecimal integer ranging from 0x0 to 0xFFFF. |
| const char *tag | Indicates the log tag, which is a string used to identify the class, file, or service behavior. |
| size_t tagLen | Indicates the length of tag. |
| const char *message | Indicates the log string. |
| size_t messageLen | Indicates the length of message. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns <b>0</b> or a larger value if the operation is successful; returns a value smaller  than <b>0</b> otherwise. |

### OH_LOG_VPrint()

```c
int OH_LOG_VPrint(LogType type, LogLevel level, unsigned int domain, const char *tag, const char *fmt, va_list ap)
```

**Description**

Outputs logs.<br> You can use this function to output logs based on the specified log type, log level, service domain, log tag, and a va_list instead of variable parameters determined by the format specifier and privacy identifier in the printf format.

**System capability**: SystemCapability.HiviewDFX.HiLog

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [LogType](capi-log-h.md#logtype) type | Indicates the log type. The type for third-party applications is defined by [LOG_APP](capi-log-h.md#logtype). |
| [LogLevel](capi-log-h.md#loglevel) level | Indicates the log level, which can be <b>LOG_DEBUG</b>, <b>LOG_INFO</b>, <b>LOG_WARN</b>, <b>LOG_ERROR</b>, and <b>LOG_FATAL</b>. |
| unsigned int domain | Indicates the service domain of logs. Its value is a hexadecimal integer ranging from 0x0 to 0xFFFF. |
| const char *tag | Indicates the log tag, which is a string used to identify the class, file, or service behavior. |
| const char *fmt | Indicates the format string, which is an enhancement of a printf format string and supports the privacy identifier. Specifically, {public} or {private} is added between the % character and the format specifier in each parameter. |
| va_list ap | Indicates a list of parameters. The number and type of parameters must map onto the format specifiers in the format string. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns <b>0</b> or a larger value if the operation is successful; returns a value smaller  than <b>0</b> otherwise. |

### OH_LOG_IsLoggable()

```c
bool OH_LOG_IsLoggable(unsigned int domain, const char *tag, LogLevel level)
```

**Description**

Checks whether logs of the specified service domain, log tag, and log level can be output.

**System capability**: SystemCapability.HiviewDFX.HiLog

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| unsigned int domain | Indicates the service domain of logs. |
| const char *tag | Indicates the log tag. |
| [LogLevel](capi-log-h.md#loglevel) level | Indicates the log level. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns <b>true</b> if the specified logs can be output; returns <b>false</b> otherwise. |

### LogCallback()

```c
typedef void (*LogCallback)(const LogType type, const LogLevel level, const unsigned int domain, const char *tag, const char *msg)
```

**Description**

Defines the function pointer type for the user-defined log processing function.

**System capability**: SystemCapability.HiviewDFX.HiLog

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const LogType](capi-log-h.md#logtype) type | Indicates the log type. The type for third-party applications is defined by [LOG_APP](capi-log-h.md#logtype). |
| [const LogLevel](capi-log-h.md#loglevel) level | Indicates the log level, which can be <b>LOG_DEBUG</b>, <b>LOG_INFO</b>, <b>LOG_WARN</b>, <b>LOG_ERROR</b>, and <b>LOG_FATAL</b>. |
| const unsigned int domain | Indicates the service domain of logs. Its value is a hexadecimal integer ranging from 0x0 to 0xFFFF. |
| const char \*tag | Indicates the log tag, which is a string used to identify the class, file, or service behavior. |
| const char \*msg | Indicates the log message itself, which is a formatted log string. |

### OH_LOG_SetCallback()

```c
void OH_LOG_SetCallback(LogCallback callback)
```

**Description**

Set the user-defined log processing function.<br> After calling this function, the callback function implemented by the user can receive all hilogs of the current process. Note that it will not change the default behavior of hilog logs of the current process, no matter whether this interface is called or not.

**System capability**: SystemCapability.HiviewDFX.HiLog

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [LogCallback](capi-log-h.md#logcallback) callback | Indicates the callback function implemented by the user. If you do not need to process hilog logs, you can transfer a null pointer. |

### OH_LOG_SetMinLogLevel()

```c
void OH_LOG_SetMinLogLevel(LogLevel level)
```

**Description**

Sets the lowest log level of the current application process.

**System capability**: SystemCapability.HiviewDFX.HiLog

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| [LogLevel](capi-log-h.md#loglevel) level | log level |

### OH_LOG_SetLogLevel()

```c
void OH_LOG_SetLogLevel(LogLevel level, PreferStrategy prefer)
```

**Description**

Sets the lowest log level of the current application process. Different preference strategy can be set.

**System capability**: SystemCapability.HiviewDFX.HiLog

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [LogLevel](capi-log-h.md#loglevel) level | log level. |
| [PreferStrategy](capi-log-h.md#preferstrategy) prefer | preference strategy. See [PreferStrategy](capi-log-h.md#preferstrategy). |


