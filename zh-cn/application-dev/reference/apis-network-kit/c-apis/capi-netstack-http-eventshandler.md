# Http_EventsHandler

```c
typedef struct Http_EventsHandler {...} Http_EventsHandler
```

## 概述

监听不同HTTP事件的回调函数。

**系统能力：** SystemCapability.Communication.NetStack

**起始版本：** 20

**相关模块：** [netstack](capi-netstack.md)

**所在头文件：** [net_http_type.h](capi-net-http-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [Http_OnDataReceiveCallback](capi-net-http-type-h.md#http_ondatareceivecallback) onDataReceive | Callback invoked when a response body is received. For details, see {@link Http_OnDataReceiveCallback}. |
| [Http_OnProgressCallback](capi-net-http-type-h.md#http_onprogresscallback) onUploadProgress | Callback invoked when an upload is triggered. For details, see {@link Http_OnProgressCallback}. |
| [Http_OnProgressCallback](capi-net-http-type-h.md#http_onprogresscallback) onDownloadProgress | Callback invoked when a download is triggered. For details, see {@link Http_OnProgressCallback}. |
| [Http_OnHeaderReceiveCallback](capi-net-http-type-h.md#http_onheaderreceivecallback) onHeadersReceive | Callback invoked when a header is received. For details, see {@link Http_OnHeaderReceiveCallback}. |
| [Http_OnVoidCallback](capi-net-http-type-h.md#http_onvoidcallback) onDataEnd | Callback invoked when the transmission is complete. For details, see {@link Http_OnVoidCallback}. |
| [Http_OnVoidCallback](capi-net-http-type-h.md#http_onvoidcallback) onCanceled | Callback invoked when the request is canceled. For details, see {@link Http_OnVoidCallback}. |


