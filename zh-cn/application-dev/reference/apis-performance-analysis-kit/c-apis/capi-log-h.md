# log.h

## 概述

定义HiLog模块的日志功能。在输出日志之前，先定义日志所属业务领域、日志标签，然后按照日志类型、日志级别选择对应接口，并指定隐私标识符。 <br> <ul><li>业务领域： 用于标识服务的子系统或模块，其值为0x0到0xFFFF的十六进制整数。 <br> <li>日志标签：字符串常量，用于标识调用所在的类或者业务。</li> <br> <li>日志级别：<b>DEBUG</b>、<b>INFO</b>、<b>WARN</b>、<b>ERROR</b>和<b>FATAL</b></li> <br> <li>参数格式：以%字符开头的printf格式字符串，包括格式说明符和可变参数。</li> <br> <li>隐私参数标识：在每个参数中%字符和格式说明符之间增加{public}、{private}标识。请注意，每个参数都有一个隐私标识符。如果未添加隐私标识符，缺省为隐私。</li></ul> <br> 示例代码：<br> 定义业务领域和日志标签：<br>     #include <hilog/log.h><br>     #define LOG_DOMAIN 0x0201<br>     #define LOG_TAG "MY_TAG"<br> 输出日志：<br>     HILOG_WARN([LOG_APP](capi-log-h.md#logtype), "Failed to visit %{private}s, reason:%{public}d.", url, errno);<br> 输出结果：<br>     05-06 15:01:06.870 1051 1051 W 0201/MY_TAG: Failed to visit <private>, reason:503.<br>

**引用文件：** <hilog/log.h>

**库：** libhilog_ndk.z.so

**系统能力：** SystemCapability.HiviewDFX.HiLog

**起始版本：** 8

**相关模块：** [HiLog](capi-hilog.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [LogType](#logtype) | LogType | 枚举日志类型。目前可用的是<b>LOG_APP</b>。 <br> |
| [LogLevel](#loglevel) | LogLevel | 日志级别枚举。建议根据各自的适用场景选择日志级别：<br> <ul><li><b>DEBUG</b>：用于调试，商业发布版本中禁用</li> <br> <li><b>INFO</b>：用于记录重要系统运行状态和关键进程中的步骤</li> <br> <li><b>WARN</b>：用于记录对用户体验影响不大且可自动恢复的意外异常。通常在检测和捕获此类异常时输出此级别的日志。</li> <br> <li><b>ERROR</b>：用于记录影响用户体验且无法自动恢复的故障</li><br> <li><b>FATAL</b>：用于记录严重影响了用户体验且不应发生的重大异常。</li></ul> <br> |
| [PreferStrategy](#preferstrategy) | PreferStrategy | 枚举在 [OH_LOG_SetLogLevel](capi-log-h.md#oh_log_setloglevel) 中使用的偏好策略。建议根据各自的适用场景选择偏好策略。 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [int OH_LOG_Print(LogType type, LogLevel level, unsigned int domain, const char *tag, const char *fmt, ...)](#oh_log_print) | - | 输出日志。使用此接口根据指定的日志类型、日志级别、业务领域、日志标签以及printf格式中格式说明符和隐私标识符确定的可变参数来输出日志。 |
| [int OH_LOG_PrintMsg(LogType type, LogLevel level, unsigned int domain, const char *tag, const char *message)](#oh_log_printmsg) | - | 输出日志。使用此接口根据指定的日志类型、日志级别、业务领域、日志标签以及printf格式中格式说明符和隐私标识符确定的va_list而不是可变参数来输出日志。 |
| [int OH_LOG_PrintMsgByLen(LogType type, LogLevel level, unsigned int domain, const char *tag, size_t tagLen, const char *message, size_t messageLen)](#oh_log_printmsgbylen) | - | 输出日志。使用此接口根据指定的日志类型、日志级别、业务领域、日志标签、消息文本和消息长度输出日志。 |
| [int OH_LOG_VPrint(LogType type, LogLevel level, unsigned int domain, const char *tag, const char *fmt, va_list ap)](#oh_log_vprint) | - | 输出日志。使用此接口根据指定的日志类型、日志级别、业务领域、日志标签以及printf格式中格式说明符和隐私标识符确定的va_list而不是可变参数来输出日志。 |
| [bool OH_LOG_IsLoggable(unsigned int domain, const char *tag, LogLevel level)](#oh_log_isloggable) | - | 检查指定业务领域、TAG、级别的日志是否可以打印。 |
| [OH_LOG_DEBUG(type, ...)((void)OH_LOG_Print((type), LOG_DEBUG, LOG_DOMAIN, LOG_TAG, __VA_ARGS__))](#oh_log_debug) | - | DEBUG级别写日志，宏封装接口。在调用此函数之前，需要先定义LOG_DOMAIN和LOG_TAG。通常，一般在源文件起始处统一定义一次。 <br> |
| [OH_LOG_INFO(type, ...)((void)OH_LOG_Print((type), LOG_INFO, LOG_DOMAIN, LOG_TAG, __VA_ARGS__))](#oh_log_info) | - | INFO级别写日志，宏封装接口。使用时需要先定义LOG_DOMAIN和LOG_TAG，一般在源文件起始处统一定义一次。 <br> |
| [OH_LOG_WARN(type, ...)((void)OH_LOG_Print((type), LOG_WARN, LOG_DOMAIN, LOG_TAG, __VA_ARGS__))](#oh_log_warn) | - | WARN级别写日志，宏封装接口。使用时需要先定义LOG_DOMAIN和LOG_TAG，一般在源文件起始处统一定义一次。 <br> |
| [OH_LOG_ERROR(type, ...)((void)OH_LOG_Print((type), LOG_ERROR, LOG_DOMAIN, LOG_TAG, __VA_ARGS__))](#oh_log_error) | - | ERROR级别写日志，宏封装接口。使用时需要先定义LOG_DOMAIN和LOG_TAG，一般在源文件起始处统一定义一次。 <br> |
| [OH_LOG_FATAL(type, ...)((void)OH_LOG_Print((type), LOG_FATAL, LOG_DOMAIN, LOG_TAG, __VA_ARGS__))](#oh_log_fatal) | - | FATAL级别写日志，宏封装接口。使用时需要先定义LOG_DOMAIN和LOG_TAG，一般在源文件起始处统一定义一次。 <br> |
| [typedef void (\*LogCallback)(const LogType type, const LogLevel level, const unsigned int domain, const char *tag, const char *msg)](#logcallback) | LogCallback | 函数指针，开发者自定义回调函数内容，在回调函数中，可自行对hilog日志进行处理。 |
| [void OH_LOG_SetCallback(LogCallback callback)](#oh_log_setcallback) | - | 注册函数。调用此函数后，用户实现的回调函数可以接收当前进程的所有hilog日志。请注意，无论是否调用该接口，它都不会更改当前进程的hilog日志的默认行为。 <br> |
| [void OH_LOG_SetMinLogLevel(LogLevel level)](#oh_log_setminloglevel) | - | 设置应用日志打印的最低日志级别。 |
| [void OH_LOG_SetLogLevel(LogLevel level, PreferStrategy prefer)](#oh_log_setloglevel) | - | 设置当前应用程序进程的最低日志级别。 |

## 枚举类型说明

### LogType

```c
enum LogType
```

**描述**

枚举日志类型。目前可用的是<b>LOG_APP</b>。 <br>

**起始版本：** 8

| 枚举项 | 描述 |
| -- | -- |
| LOG_APP = 0 | 第三方应用日志 |

### LogLevel

```c
enum LogLevel
```

**描述**

日志级别枚举。建议根据各自的适用场景选择日志级别：<br> <ul><li><b>DEBUG</b>：用于调试，商业发布版本中禁用</li> <br> <li><b>INFO</b>：用于记录重要系统运行状态和关键进程中的步骤</li> <br> <li><b>WARN</b>：用于记录对用户体验影响不大且可自动恢复的意外异常。通常在检测和捕获此类异常时输出此级别的日志。</li> <br> <li><b>ERROR</b>：用于记录影响用户体验且无法自动恢复的故障</li><br> <li><b>FATAL</b>：用于记录严重影响了用户体验且不应发生的重大异常。</li></ul> <br>

**起始版本：** 8

| 枚举项 | 描述 |
| -- | -- |
| LOG_DEBUG = 3 | DEBUG日志级别，使用[OH_LOG_DEBUG](capi-log-h.md#oh_log_debug)接口打印。 |
| LOG_INFO = 4 | INFO日志级别，使用[OH_LOG_INFO](capi-log-h.md#oh_log_info)接口打印。 |
| LOG_WARN = 5 | WARN日志级别，使用[OH_LOG_WARN](capi-log-h.md#oh_log_warn)接口打印。 |
| LOG_ERROR = 6 | ERROR日志级别，使用[OH_LOG_ERROR](capi-log-h.md#oh_log_error)接口打印。 |
| LOG_FATAL = 7 | FATAL日志级别，使用[OH_LOG_FATAL](capi-log-h.md#oh_log_fatal)接口打印。 |

### PreferStrategy

```c
enum PreferStrategy
```

**描述**

枚举在 [OH_LOG_SetLogLevel](capi-log-h.md#oh_log_setloglevel) 中使用的偏好策略。建议根据各自的适用场景选择偏好策略。

**起始版本：** 21

| 枚举项 | 描述 |
| -- | -- |
| UNSET_LOGLEVEL = 0 | 清除日志级别设置 |
| PREFER_CLOSE_LOG = 1 | 实际生效的最低日志级别是新设置的级别和系统控制的最低级别两个值的较大值。等效于调用OH_LOG_SetMinLogLevel。 |
| PREFER_OPEN_LOG = 2 | 实际生效的最低日志级别是新设置的级别和系统控制的最低级别两个值的较小值。 |


## 函数说明

### OH_LOG_Print()

```c
int OH_LOG_Print(LogType type, LogLevel level, unsigned int domain, const char *tag, const char *fmt, ...)
```

**描述**

输出日志。使用此接口根据指定的日志类型、日志级别、业务领域、日志标签以及printf格式中格式说明符和隐私标识符确定的可变参数来输出日志。

**起始版本：** 8

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [LogType](capi-log-h.md#logtype) type | 日志类型，三方应用日志类型为[LOG_APP](capi-log-h.md#logtype)。 |
| [LogLevel](capi-log-h.md#loglevel) level | 日志级别，日志级别包括<b>LOG_DEBUG</b>, <b>LOG_INFO</b>, <b>LOG_WARN</b>, <b>LOG_ERROR</b>, and <b>LOG_FATAL</b>. |
| unsigned int domain | 日志业务领域，16进制整数，范围0x0~0xFFFF。 |
| const char *tag | 日志标签，这是一个用于标识调用所在的类或者业务的字符串。 |
| const char *fmt | 格式化字符串，基于类printf格式的增强，支持隐私参数标识，即在格式字符串每个参数中'%'符号后类型前增加{public}、{private}标识。 |
| [](capi-log-h.md#).[](capi-log-h.md#).[](capi-log-h.md#).[](capi-log-h.md#) | 参数列表，参数数目、参数类型必须与格式字符串中的标识一一对应。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 大于等于<b>0</b>表示成功；小于<b>0</b>表示失败。 |

### OH_LOG_PrintMsg()

```c
int OH_LOG_PrintMsg(LogType type, LogLevel level, unsigned int domain, const char *tag, const char *message)
```

**描述**

输出日志。使用此接口根据指定的日志类型、日志级别、业务领域、日志标签以及printf格式中格式说明符和隐私标识符确定的va_list而不是可变参数来输出日志。

**起始版本：** 18

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [LogType](capi-log-h.md#logtype) type | 日志类型，三方应用日志类型为[LOG_APP](capi-log-h.md#logtype)。 |
| [LogLevel](capi-log-h.md#loglevel) level | 日志级别，日志级别包括<b>LOG_DEBUG</b>, <b>LOG_INFO</b>, <b>LOG_WARN</b>, <b>LOG_ERROR</b>, and <b>LOG_FATAL</b>. |
| unsigned int domain | 日志业务领域，16进制整数，范围0x0~0xFFFF。 |
| const char *tag | 日志标签，这是一个用于标识调用所在的类或者业务的字符串。 |
| const char *message | 日志字符串。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 大于等于<b>0</b>表示成功；小于<b>0</b>表示失败。 |

### OH_LOG_PrintMsgByLen()

```c
int OH_LOG_PrintMsgByLen(LogType type, LogLevel level, unsigned int domain, const char *tag, size_t tagLen, const char *message, size_t messageLen)
```

**描述**

输出日志。使用此接口根据指定的日志类型、日志级别、业务领域、日志标签、消息文本和消息长度输出日志。

**起始版本：** 18

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [LogType](capi-log-h.md#logtype) type | 日志类型，三方应用日志类型为[LOG_APP](capi-log-h.md#logtype)。 |
| [LogLevel](capi-log-h.md#loglevel) level | 日志级别，日志级别包括<b>LOG_DEBUG</b>, <b>LOG_INFO</b>, <b>LOG_WARN</b>, <b>LOG_ERROR</b>, and <b>LOG_FATAL</b>. |
| unsigned int domain | 日志业务领域，16进制整数，范围0x0~0xFFFF。 |
| const char *tag | 日志标签，这是一个用于标识调用所在的类或者业务的字符串。 |
| size_t tagLen | 标签长度。 |
| const char *message | 日志字符串。 |
| size_t messageLen | 日志字符串长度。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 大于等于<b>0</b>表示成功；小于<b>0</b>表示失败。 |

### OH_LOG_VPrint()

```c
int OH_LOG_VPrint(LogType type, LogLevel level, unsigned int domain, const char *tag, const char *fmt, va_list ap)
```

**描述**

输出日志。使用此接口根据指定的日志类型、日志级别、业务领域、日志标签以及printf格式中格式说明符和隐私标识符确定的va_list而不是可变参数来输出日志。

**起始版本：** 18

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [LogType](capi-log-h.md#logtype) type | 日志类型，三方应用日志类型为[LOG_APP](capi-log-h.md#logtype)。 |
| [LogLevel](capi-log-h.md#loglevel) level | 日志级别，日志级别包括<b>LOG_DEBUG</b>, <b>LOG_INFO</b>, <b>LOG_WARN</b>, <b>LOG_ERROR</b>, and <b>LOG_FATAL</b>。 |
| unsigned int domain | 日志业务领域，16进制整数，范围0x0~0xFFFF。 |
| const char *tag | 日志标签，这是一个用于标识调用所在的类或者业务的字符串。 |
| const char *fmt | 格式化字符串，基于类printf格式的增强，支持隐私参数标识，即在格式字符串每个参数中符号后类型前增加{public}、{private}标识。 |
| va_list ap | 参数列表。参数数目、参数类型必须与格式字符串中的格式说明符对应。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int | 大于等于<b>0</b>表示成功；小于<b>0</b>表示失败。 |

### OH_LOG_IsLoggable()

```c
bool OH_LOG_IsLoggable(unsigned int domain, const char *tag, LogLevel level)
```

**描述**

检查指定业务领域、TAG、级别的日志是否可以打印。

**起始版本：** 8

**参数：**

| 参数项 | 描述 |
| -- | -- |
| unsigned int domain | 日志业务领域，16进制整数，范围0x0~0xFFFF。 |
| const char *tag | 日志标签，这是一个用于标识调用所在的类或者业务的字符串。 |
| [LogLevel](capi-log-h.md#loglevel) level | 日志级别，日志级别包括<b>LOG_DEBUG</b>, <b>LOG_INFO</b>, <b>LOG_WARN</b>, <b>LOG_ERROR</b>, and <b>LOG_FATAL</b>. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| bool | 如果指定的日志可以输出，返回<b>true</b>；否则返回<b>false</b>。 |

### OH_LOG_DEBUG()

```c
OH_LOG_DEBUG(type, ...)((void)OH_LOG_Print((type), LOG_DEBUG, LOG_DOMAIN, LOG_TAG, __VA_ARGS__))
```

**描述**

DEBUG级别写日志，宏封装接口。在调用此函数之前，需要先定义LOG_DOMAIN和LOG_TAG。通常，一般在源文件起始处统一定义一次。 <br>

**起始版本：** 8

**参数：**

| 参数项 | 描述 |
| -- | -- |
| type | 日志类型，三方应用日志类型为[LOG_APP](capi-log-h.md#logtype)。 |
| fmt | 格式化字符串，基于类printf格式的增强，支持隐私参数标识，即在格式字符串每个参数中符号后类型前增加{public}、{private}标识。 |
| ... | 与格式字符串里参数类型对应的参数列表，参数数目、参数类型必须与格式字符串中的标识一一对应。 |

**参考：**

[OH_LOG_Print](capi-log-h.md#oh_log_print)


### OH_LOG_INFO()

```c
OH_LOG_INFO(type, ...)((void)OH_LOG_Print((type), LOG_INFO, LOG_DOMAIN, LOG_TAG, __VA_ARGS__))
```

**描述**

INFO级别写日志，宏封装接口。使用时需要先定义LOG_DOMAIN和LOG_TAG，一般在源文件起始处统一定义一次。 <br>

**起始版本：** 8

**参数：**

| 参数项 | 描述 |
| -- | -- |
| type | 日志类型，三方应用日志类型为[LOG_APP](capi-log-h.md#logtype)。 |
| fmt | 格式化字符串，基于类printf格式的增强，支持隐私参数标识，即在格式字符串每个参数中符号后类型前增加{public}、{private}标识。 |
| ... | 与格式字符串里参数类型对应的参数列表，参数数目、参数类型必须与格式字符串中的标识一一对应。 |

**参考：**

[OH_LOG_Print](capi-log-h.md#oh_log_print)


### OH_LOG_WARN()

```c
OH_LOG_WARN(type, ...)((void)OH_LOG_Print((type), LOG_WARN, LOG_DOMAIN, LOG_TAG, __VA_ARGS__))
```

**描述**

WARN级别写日志，宏封装接口。使用时需要先定义LOG_DOMAIN和LOG_TAG，一般在源文件起始处统一定义一次。 <br>

**起始版本：** 8

**参数：**

| 参数项 | 描述 |
| -- | -- |
| type | 日志类型，三方应用日志类型为[LOG_APP](capi-log-h.md#logtype)。 |
| fmt | 格式化字符串，基于类printf格式的增强，支持隐私参数标识，即在格式字符串每个参数中符号后类型前增加{public}、{private}标识。 |
| ... | 与格式字符串里参数类型对应的参数列表，参数数目、参数类型必须与格式字符串中的标识一一对应。 |

**参考：**

[OH_LOG_Print](capi-log-h.md#oh_log_print)


### OH_LOG_ERROR()

```c
OH_LOG_ERROR(type, ...)((void)OH_LOG_Print((type), LOG_ERROR, LOG_DOMAIN, LOG_TAG, __VA_ARGS__))
```

**描述**

ERROR级别写日志，宏封装接口。使用时需要先定义LOG_DOMAIN和LOG_TAG，一般在源文件起始处统一定义一次。 <br>

**起始版本：** 8

**参数：**

| 参数项 | 描述 |
| -- | -- |
| type | 日志类型，三方应用日志类型为[LOG_APP](capi-log-h.md#logtype)。 |
| fmt | 格式化字符串，基于类printf格式的增强，支持隐私参数标识，即在格式字符串每个参数中符号后类型前增加{public}、{private}标识。 |
| ... | 与格式字符串里参数类型对应的参数列表，参数数目、参数类型必须与格式字符串中的标识一一对应。 |

**参考：**

[OH_LOG_Print](capi-log-h.md#oh_log_print)


### OH_LOG_FATAL()

```c
OH_LOG_FATAL(type, ...)((void)OH_LOG_Print((type), LOG_FATAL, LOG_DOMAIN, LOG_TAG, __VA_ARGS__))
```

**描述**

FATAL级别写日志，宏封装接口。使用时需要先定义LOG_DOMAIN和LOG_TAG，一般在源文件起始处统一定义一次。 <br>

**起始版本：** 8

**参数：**

| 参数项 | 描述 |
| -- | -- |
| type | 日志类型，三方应用日志类型为[LOG_APP](capi-log-h.md#logtype)。 |
| fmt | 格式化字符串，基于类printf格式的增强，支持隐私参数标识，即在格式字符串每个参数中符号后类型前增加{public}、{private}标识。 |
| ... | 与格式字符串里参数类型对应的参数列表，参数数目、参数类型必须与格式字符串中的标识一一对应。 |

**参考：**

[OH_LOG_Print](capi-log-h.md#oh_log_print)


### LogCallback()

```c
typedef void (*LogCallback)(const LogType type, const LogLevel level, const unsigned int domain, const char *tag, const char *msg)
```

**描述**

函数指针，开发者自定义回调函数内容，在回调函数中，可自行对hilog日志进行处理。

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const LogType](capi-log-h.md#logtype) type | 日志类型，三方应用日志类型为[LOG_APP](capi-log-h.md#logtype)。 |
| [const LogLevel](capi-log-h.md#loglevel) level | 日志级别，日志级别包括<b>LOG_DEBUG</b>, <b>LOG_INFO</b>, <b>LOG_WARN</b>, <b>LOG_ERROR</b>, and <b>LOG_FATAL</b>。 |
| const unsigned int domain | 日志业务领域，16进制整数，范围0x0~0xFFFF。 |
| const char \*tag | 日志标签，这是一个用于标识调用所在的类或者业务的字符串。 |
| const char \*msg | 日志内容，格式化之后的日志字符串。 |

### OH_LOG_SetCallback()

```c
void OH_LOG_SetCallback(LogCallback callback)
```

**描述**

注册函数。调用此函数后，用户实现的回调函数可以接收当前进程的所有hilog日志。请注意，无论是否调用该接口，它都不会更改当前进程的hilog日志的默认行为。 <br>

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [LogCallback](capi-log-h.md#logcallback) callback | 用户实现的回调函数。如果不需要处理hilog日志，可以传输空指针。 |

### OH_LOG_SetMinLogLevel()

```c
void OH_LOG_SetMinLogLevel(LogLevel level)
```

**描述**

设置应用日志打印的最低日志级别。

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [LogLevel](capi-log-h.md#loglevel) level | 日志级别。 |

### OH_LOG_SetLogLevel()

```c
void OH_LOG_SetLogLevel(LogLevel level, PreferStrategy prefer)
```

**描述**

设置当前应用程序进程的最低日志级别。

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [LogLevel](capi-log-h.md#loglevel) level | 日志级别。 |
| [PreferStrategy](capi-log-h.md#preferstrategy) prefer | 偏好策略。参见 [PreferStrategy](capi-log-h.md#preferstrategy)。 |


