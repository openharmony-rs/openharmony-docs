# WebDownloadErrorCode

下载任务的错误码。

**起始版本：** 11

<!--Device-webview-enum WebDownloadErrorCode--><!--Device-webview-enum WebDownloadErrorCode-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## ERROR_UNKNOWN

```TypeScript
ERROR_UNKNOWN = 0
```

未知的错误。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebDownloadErrorCode-ERROR_UNKNOWN = 0--><!--Device-WebDownloadErrorCode-ERROR_UNKNOWN = 0-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## FILE_FAILED

```TypeScript
FILE_FAILED = 1
```

常规文件操作失败。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebDownloadErrorCode-FILE_FAILED = 1--><!--Device-WebDownloadErrorCode-FILE_FAILED = 1-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## FILE_ACCESS_DENIED

```TypeScript
FILE_ACCESS_DENIED = 2
```

没有权限访问文件。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebDownloadErrorCode-FILE_ACCESS_DENIED = 2--><!--Device-WebDownloadErrorCode-FILE_ACCESS_DENIED = 2-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## FILE_NO_SPACE

```TypeScript
FILE_NO_SPACE = 3
```

磁盘没有足够的空间。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebDownloadErrorCode-FILE_NO_SPACE = 3--><!--Device-WebDownloadErrorCode-FILE_NO_SPACE = 3-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## FILE_NAME_TOO_LONG

```TypeScript
FILE_NAME_TOO_LONG = 5
```

文件名过长。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebDownloadErrorCode-FILE_NAME_TOO_LONG = 5--><!--Device-WebDownloadErrorCode-FILE_NAME_TOO_LONG = 5-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## FILE_TOO_LARGE

```TypeScript
FILE_TOO_LARGE = 6
```

文件太大。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebDownloadErrorCode-FILE_TOO_LARGE = 6--><!--Device-WebDownloadErrorCode-FILE_TOO_LARGE = 6-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## FILE_TRANSIENT_ERROR

```TypeScript
FILE_TRANSIENT_ERROR = 10
```

出现了一些临时问题，例如内存不足、文件正在使用以及同时打开的文件过多。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebDownloadErrorCode-FILE_TRANSIENT_ERROR = 10--><!--Device-WebDownloadErrorCode-FILE_TRANSIENT_ERROR = 10-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## FILE_BLOCKED

```TypeScript
FILE_BLOCKED = 11
```

由于某些本地策略，文件被阻止访问。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebDownloadErrorCode-FILE_BLOCKED = 11--><!--Device-WebDownloadErrorCode-FILE_BLOCKED = 11-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## FILE_TOO_SHORT

```TypeScript
FILE_TOO_SHORT = 13
```

当尝试恢复下载时，发现文件不够长，可能该文件已不存在。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebDownloadErrorCode-FILE_TOO_SHORT = 13--><!--Device-WebDownloadErrorCode-FILE_TOO_SHORT = 13-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## FILE_HASH_MISMATCH

```TypeScript
FILE_HASH_MISMATCH = 14
```

哈希不匹配。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebDownloadErrorCode-FILE_HASH_MISMATCH = 14--><!--Device-WebDownloadErrorCode-FILE_HASH_MISMATCH = 14-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## FILE_SAME_AS_SOURCE

```TypeScript
FILE_SAME_AS_SOURCE = 15
```

文件已存在。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebDownloadErrorCode-FILE_SAME_AS_SOURCE = 15--><!--Device-WebDownloadErrorCode-FILE_SAME_AS_SOURCE = 15-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## NETWORK_FAILED

```TypeScript
NETWORK_FAILED = 20
```

一般网络错误。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebDownloadErrorCode-NETWORK_FAILED = 20--><!--Device-WebDownloadErrorCode-NETWORK_FAILED = 20-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## NETWORK_TIMEOUT

```TypeScript
NETWORK_TIMEOUT = 21
```

网络超时。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebDownloadErrorCode-NETWORK_TIMEOUT = 21--><!--Device-WebDownloadErrorCode-NETWORK_TIMEOUT = 21-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## NETWORK_DISCONNECTED

```TypeScript
NETWORK_DISCONNECTED = 22
```

网络断开连接。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebDownloadErrorCode-NETWORK_DISCONNECTED = 22--><!--Device-WebDownloadErrorCode-NETWORK_DISCONNECTED = 22-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## NETWORK_SERVER_DOWN

```TypeScript
NETWORK_SERVER_DOWN = 23
```

服务器关闭。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebDownloadErrorCode-NETWORK_SERVER_DOWN = 23--><!--Device-WebDownloadErrorCode-NETWORK_SERVER_DOWN = 23-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## NETWORK_INVALID_REQUEST

```TypeScript
NETWORK_INVALID_REQUEST = 24
```

无效的网络请求，可能重定向到不支持的方案或无效的URL。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebDownloadErrorCode-NETWORK_INVALID_REQUEST = 24--><!--Device-WebDownloadErrorCode-NETWORK_INVALID_REQUEST = 24-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## SERVER_FAILED

```TypeScript
SERVER_FAILED = 30
```

服务器返回了一个一般性错误。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebDownloadErrorCode-SERVER_FAILED = 30--><!--Device-WebDownloadErrorCode-SERVER_FAILED = 30-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## SERVER_NO_RANGE

```TypeScript
SERVER_NO_RANGE = 31
```

服务器不支持范围请求。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebDownloadErrorCode-SERVER_NO_RANGE = 31--><!--Device-WebDownloadErrorCode-SERVER_NO_RANGE = 31-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## SERVER_BAD_CONTENT

```TypeScript
SERVER_BAD_CONTENT = 33
```

服务器没有请求的数据。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebDownloadErrorCode-SERVER_BAD_CONTENT = 33--><!--Device-WebDownloadErrorCode-SERVER_BAD_CONTENT = 33-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## SERVER_UNAUTHORIZED

```TypeScript
SERVER_UNAUTHORIZED = 34
```

服务器不允许下载该文件。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebDownloadErrorCode-SERVER_UNAUTHORIZED = 34--><!--Device-WebDownloadErrorCode-SERVER_UNAUTHORIZED = 34-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## SERVER_CERT_PROBLEM

```TypeScript
SERVER_CERT_PROBLEM = 35
```

服务器证书错误。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebDownloadErrorCode-SERVER_CERT_PROBLEM = 35--><!--Device-WebDownloadErrorCode-SERVER_CERT_PROBLEM = 35-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## SERVER_FORBIDDEN

```TypeScript
SERVER_FORBIDDEN = 36
```

服务器访问被禁止。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebDownloadErrorCode-SERVER_FORBIDDEN = 36--><!--Device-WebDownloadErrorCode-SERVER_FORBIDDEN = 36-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## SERVER_UNREACHABLE

```TypeScript
SERVER_UNREACHABLE = 37
```

无法访问服务器。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebDownloadErrorCode-SERVER_UNREACHABLE = 37--><!--Device-WebDownloadErrorCode-SERVER_UNREACHABLE = 37-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## SERVER_CONTENT_LENGTH_MISMATCH

```TypeScript
SERVER_CONTENT_LENGTH_MISMATCH = 38
```

接收到的数据与内容长度不匹配。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebDownloadErrorCode-SERVER_CONTENT_LENGTH_MISMATCH = 38--><!--Device-WebDownloadErrorCode-SERVER_CONTENT_LENGTH_MISMATCH = 38-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## SERVER_CROSS_ORIGIN_REDIRECT

```TypeScript
SERVER_CROSS_ORIGIN_REDIRECT = 39
```

发生意外的跨站重定向。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebDownloadErrorCode-SERVER_CROSS_ORIGIN_REDIRECT = 39--><!--Device-WebDownloadErrorCode-SERVER_CROSS_ORIGIN_REDIRECT = 39-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## USER_CANCELED

```TypeScript
USER_CANCELED = 40
```

用户取消了下载。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebDownloadErrorCode-USER_CANCELED = 40--><!--Device-WebDownloadErrorCode-USER_CANCELED = 40-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## USER_SHUTDOWN

```TypeScript
USER_SHUTDOWN = 41
```

用户关闭了应用。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebDownloadErrorCode-USER_SHUTDOWN = 41--><!--Device-WebDownloadErrorCode-USER_SHUTDOWN = 41-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## CRASH

```TypeScript
CRASH = 50
```

应用发生了崩溃。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebDownloadErrorCode-CRASH = 50--><!--Device-WebDownloadErrorCode-CRASH = 50-End-->

**系统能力：** SystemCapability.Web.Webview.Core

