# 常量

## ERROR_CANNOT_RESUME

```TypeScript
const ERROR_CANNOT_RESUME: number
```

下载任务错误码：网络原因导致恢复下载失败。

**起始版本：** 7

<!--Device-request-const ERROR_CANNOT_RESUME: int--><!--Device-request-const ERROR_CANNOT_RESUME: int-End-->

**系统能力：** SystemCapability.MiscServices.Download

## ERROR_DEVICE_NOT_FOUND

```TypeScript
const ERROR_DEVICE_NOT_FOUND: number
```

下载任务错误码：找不到SD卡等存储设备。

**起始版本：** 7

<!--Device-request-const ERROR_DEVICE_NOT_FOUND: int--><!--Device-request-const ERROR_DEVICE_NOT_FOUND: int-End-->

**系统能力：** SystemCapability.MiscServices.Download

## ERROR_FILE_ALREADY_EXISTS

```TypeScript
const ERROR_FILE_ALREADY_EXISTS: number
```

下载任务错误码：要下载的文件已存在，下载会话无法覆盖现有文件。

**起始版本：** 7

<!--Device-request-const ERROR_FILE_ALREADY_EXISTS: int--><!--Device-request-const ERROR_FILE_ALREADY_EXISTS: int-End-->

**系统能力：** SystemCapability.MiscServices.Download

## ERROR_FILE_ERROR

```TypeScript
const ERROR_FILE_ERROR: number
```

下载任务错误码：文件操作失败。

**起始版本：** 7

<!--Device-request-const ERROR_FILE_ERROR: int--><!--Device-request-const ERROR_FILE_ERROR: int-End-->

**系统能力：** SystemCapability.MiscServices.Download

## ERROR_HTTP_DATA_ERROR

```TypeScript
const ERROR_HTTP_DATA_ERROR: number
```

下载任务错误码：HTTP传输失败。

**起始版本：** 7

<!--Device-request-const ERROR_HTTP_DATA_ERROR: int--><!--Device-request-const ERROR_HTTP_DATA_ERROR: int-End-->

**系统能力：** SystemCapability.MiscServices.Download

## ERROR_INSUFFICIENT_SPACE

```TypeScript
const ERROR_INSUFFICIENT_SPACE: number
```

下载任务错误码：存储空间不足。

**起始版本：** 7

<!--Device-request-const ERROR_INSUFFICIENT_SPACE: int--><!--Device-request-const ERROR_INSUFFICIENT_SPACE: int-End-->

**系统能力：** SystemCapability.MiscServices.Download

## ERROR_OFFLINE

```TypeScript
const ERROR_OFFLINE: number
```

下载任务错误码：网络未连接。

**起始版本：** 9

<!--Device-request-const ERROR_OFFLINE: int--><!--Device-request-const ERROR_OFFLINE: int-End-->

**系统能力：** SystemCapability.MiscServices.Download

## ERROR_TOO_MANY_REDIRECTS

```TypeScript
const ERROR_TOO_MANY_REDIRECTS: number
```

下载任务错误码：网络重定向过多导致的错误。

**起始版本：** 7

<!--Device-request-const ERROR_TOO_MANY_REDIRECTS: int--><!--Device-request-const ERROR_TOO_MANY_REDIRECTS: int-End-->

**系统能力：** SystemCapability.MiscServices.Download

## ERROR_UNHANDLED_HTTP_CODE

```TypeScript
const ERROR_UNHANDLED_HTTP_CODE: number
```

下载任务错误码：无法识别的HTTP代码。

**起始版本：** 7

<!--Device-request-const ERROR_UNHANDLED_HTTP_CODE: int--><!--Device-request-const ERROR_UNHANDLED_HTTP_CODE: int-End-->

**系统能力：** SystemCapability.MiscServices.Download

## ERROR_UNKNOWN

```TypeScript
const ERROR_UNKNOWN: number
```

下载任务错误码：未知错误。

例如：API version 12及以下版本，系统仅支持串行地尝试连接域名相关IP，不支持单个IP的连接时间控制。若DNS返回的首个IP被阻塞，可能会由于握手超时导致ERROR_UNKNOWN错误。

**起始版本：** 7

<!--Device-request-const ERROR_UNKNOWN: int--><!--Device-request-const ERROR_UNKNOWN: int-End-->

**系统能力：** SystemCapability.MiscServices.Download

## ERROR_UNSUPPORTED_NETWORK_TYPE

```TypeScript
const ERROR_UNSUPPORTED_NETWORK_TYPE: number
```

下载任务错误码：网络类型不匹配。

**起始版本：** 9

<!--Device-request-const ERROR_UNSUPPORTED_NETWORK_TYPE: int--><!--Device-request-const ERROR_UNSUPPORTED_NETWORK_TYPE: int-End-->

**系统能力：** SystemCapability.MiscServices.Download

## EXCEPTION_FILEIO

```TypeScript
const EXCEPTION_FILEIO: number
```

特有错误码：文件操作异常。

**起始版本：** 9

<!--Device-request-const EXCEPTION_FILEIO: int--><!--Device-request-const EXCEPTION_FILEIO: int-End-->

**系统能力：** SystemCapability.MiscServices.Download

## EXCEPTION_FILEPATH

```TypeScript
const EXCEPTION_FILEPATH: number
```

特有错误码：文件路径异常。

**起始版本：** 9

<!--Device-request-const EXCEPTION_FILEPATH: int--><!--Device-request-const EXCEPTION_FILEPATH: int-End-->

**系统能力：** SystemCapability.MiscServices.Download

## EXCEPTION_OTHERS

```TypeScript
const EXCEPTION_OTHERS: number
```

特有错误码：其他错误。

**起始版本：** 9

<!--Device-request-const EXCEPTION_OTHERS: int--><!--Device-request-const EXCEPTION_OTHERS: int-End-->

**系统能力：** SystemCapability.MiscServices.Download

## EXCEPTION_PARAMCHECK

```TypeScript
const EXCEPTION_PARAMCHECK: number
```

通用错误码：参数检查失败。

**起始版本：** 9

<!--Device-request-const EXCEPTION_PARAMCHECK: int--><!--Device-request-const EXCEPTION_PARAMCHECK: int-End-->

**系统能力：** SystemCapability.MiscServices.Download

## EXCEPTION_PERMISSION

```TypeScript
const EXCEPTION_PERMISSION: number
```

通用错误码：权限校验失败。

**起始版本：** 9

<!--Device-request-const EXCEPTION_PERMISSION: int--><!--Device-request-const EXCEPTION_PERMISSION: int-End-->

**系统能力：** SystemCapability.MiscServices.Download

## EXCEPTION_SERVICE

```TypeScript
const EXCEPTION_SERVICE: number
```

特有错误码：服务异常。

**起始版本：** 9

<!--Device-request-const EXCEPTION_SERVICE: int--><!--Device-request-const EXCEPTION_SERVICE: int-End-->

**系统能力：** SystemCapability.MiscServices.Download

## EXCEPTION_UNSUPPORTED

```TypeScript
const EXCEPTION_UNSUPPORTED: number
```

通用错误码：该设备不支持此API。

**起始版本：** 9

<!--Device-request-const EXCEPTION_UNSUPPORTED: int--><!--Device-request-const EXCEPTION_UNSUPPORTED: int-End-->

**系统能力：** SystemCapability.MiscServices.Download

## NETWORK_MOBILE

```TypeScript
const NETWORK_MOBILE: number
```

网络类型：使用蜂窝网络时允许下载的位标志。

**起始版本：** 6

<!--Device-request-const NETWORK_MOBILE: int--><!--Device-request-const NETWORK_MOBILE: int-End-->

**系统能力：** SystemCapability.MiscServices.Download

## NETWORK_WIFI

```TypeScript
const NETWORK_WIFI: number
```

网络类型：使用WLAN时允许下载的位标志。

**起始版本：** 6

<!--Device-request-const NETWORK_WIFI: int--><!--Device-request-const NETWORK_WIFI: int-End-->

**系统能力：** SystemCapability.MiscServices.Download

## PAUSED_BY_USER

```TypeScript
const PAUSED_BY_USER: number
```

下载任务暂停原因：用户暂停会话。

**起始版本：** 9

<!--Device-request-const PAUSED_BY_USER: int--><!--Device-request-const PAUSED_BY_USER: int-End-->

**系统能力：** SystemCapability.MiscServices.Download

## PAUSED_QUEUED_FOR_WIFI

```TypeScript
const PAUSED_QUEUED_FOR_WIFI: number
```

下载任务暂停原因：文件大小超过了使用蜂窝网络会话允许的最大值，下载被暂停并等待WLAN连接。

**起始版本：** 7

<!--Device-request-const PAUSED_QUEUED_FOR_WIFI: int--><!--Device-request-const PAUSED_QUEUED_FOR_WIFI: int-End-->

**系统能力：** SystemCapability.MiscServices.Download

## PAUSED_UNKNOWN

```TypeScript
const PAUSED_UNKNOWN: number
```

下载任务暂停原因：未知原因导致暂停下载。

**起始版本：** 7

<!--Device-request-const PAUSED_UNKNOWN: int--><!--Device-request-const PAUSED_UNKNOWN: int-End-->

**系统能力：** SystemCapability.MiscServices.Download

## PAUSED_WAITING_FOR_NETWORK

```TypeScript
const PAUSED_WAITING_FOR_NETWORK: number
```

下载任务暂停原因：网络问题导致下载暂停。

例如：网络断开。

**起始版本：** 7

<!--Device-request-const PAUSED_WAITING_FOR_NETWORK: int--><!--Device-request-const PAUSED_WAITING_FOR_NETWORK: int-End-->

**系统能力：** SystemCapability.MiscServices.Download

## PAUSED_WAITING_TO_RETRY

```TypeScript
const PAUSED_WAITING_TO_RETRY: number
```

下载任务暂停原因：网络错误导致下载会话将被重试。

**起始版本：** 7

<!--Device-request-const PAUSED_WAITING_TO_RETRY: int--><!--Device-request-const PAUSED_WAITING_TO_RETRY: int-End-->

**系统能力：** SystemCapability.MiscServices.Download

## SESSION_FAILED

```TypeScript
const SESSION_FAILED: number
```

下载任务状态码：下载会话已失败，将不会重试。

**起始版本：** 7

<!--Device-request-const SESSION_FAILED: int--><!--Device-request-const SESSION_FAILED: int-End-->

**系统能力：** SystemCapability.MiscServices.Download

## SESSION_PAUSED

```TypeScript
const SESSION_PAUSED: number
```

下载任务状态码：下载会话已暂停。

**起始版本：** 7

<!--Device-request-const SESSION_PAUSED: int--><!--Device-request-const SESSION_PAUSED: int-End-->

**系统能力：** SystemCapability.MiscServices.Download

## SESSION_PENDING

```TypeScript
const SESSION_PENDING: number
```

下载任务状态码：下载会话正在被调度中。

**起始版本：** 7

<!--Device-request-const SESSION_PENDING: int--><!--Device-request-const SESSION_PENDING: int-End-->

**系统能力：** SystemCapability.MiscServices.Download

## SESSION_RUNNING

```TypeScript
const SESSION_RUNNING: number
```

下载任务状态码：下载会话正在进行中。

**起始版本：** 7

<!--Device-request-const SESSION_RUNNING: int--><!--Device-request-const SESSION_RUNNING: int-End-->

**系统能力：** SystemCapability.MiscServices.Download

## SESSION_SUCCESSFUL

```TypeScript
const SESSION_SUCCESSFUL: number
```

下载任务状态码：下载会话已完成。

**起始版本：** 7

<!--Device-request-const SESSION_SUCCESSFUL: int--><!--Device-request-const SESSION_SUCCESSFUL: int-End-->

**系统能力：** SystemCapability.MiscServices.Download

