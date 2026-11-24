# Http_EventsHandler

```c
typedef struct Http_EventsHandler {...} Http_EventsHandler
```

## 概述

监听不同HTTP事件的回调函数。

<!--Device-struct Http_EventsHandler {...}--><!--Device-struct Http_EventsHandler {...}-End-->

**系统能力：** SystemCapability.Communication.NetStack

**起始版本：** 20

**相关模块：** [netstack](capi-network-kit-netstack.md)

**所在头文件：** [net_http_type.h](capi-net-http-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [Http_OnDataReceiveCallback](capi-net-http-type-h.md#http_ondatareceivecallback) onDataReceive | 收到响应体时的回调函数，参考[Http_OnDataReceiveCallback](capi-net-http-type-h.md#http_ondatareceivecallback)。<br><!--Device-Http_OnDataReceiveCallback onDataReceive--><!--Device-Http_OnDataReceiveCallback onDataReceive-End--> |
| [Http_OnProgressCallback](capi-net-http-type-h.md#http_onprogresscallback) onUploadProgress | 上传时调用的回调函数，参考[Http_OnProgressCallback](capi-net-http-type-h.md#http_onprogresscallback)。<br><!--Device-Http_OnProgressCallback onUploadProgress--><!--Device-Http_OnProgressCallback onUploadProgress-End--> |
| [Http_OnProgressCallback](capi-net-http-type-h.md#http_onprogresscallback) onDownloadProgress | 下载时调用的回调函数，参考[Http_OnProgressCallback](capi-net-http-type-h.md#http_onprogresscallback)。<br><!--Device-Http_OnProgressCallback onDownloadProgress--><!--Device-Http_OnProgressCallback onDownloadProgress-End--> |
| [Http_OnHeaderReceiveCallback](capi-net-http-type-h.md#http_onheaderreceivecallback) onHeadersReceive | 收到header时的回调函数，参考[Http_OnHeaderReceiveCallback](capi-net-http-type-h.md#http_onheaderreceivecallback)。<br><!--Device-Http_OnHeaderReceiveCallback onHeadersReceive--><!--Device-Http_OnHeaderReceiveCallback onHeadersReceive-End--> |
| [Http_OnVoidCallback](capi-net-http-type-h.md#http_onvoidcallback) onDataEnd | 传输结束时的回调函数，参考[Http_OnVoidCallback](capi-net-http-type-h.md#http_onvoidcallback)。<br><!--Device-Http_OnVoidCallback onDataEnd--><!--Device-Http_OnVoidCallback onDataEnd-End--> |
| [Http_OnVoidCallback](capi-net-http-type-h.md#http_onvoidcallback) onCanceled | 请求被取消时的回调函数，参考[Http_OnVoidCallback](capi-net-http-type-h.md#http_onvoidcallback)。<br><!--Device-Http_OnVoidCallback onCanceled--><!--Device-Http_OnVoidCallback onCanceled-End--> |


