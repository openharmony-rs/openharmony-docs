# WebResourceType

Defines the resource type of request.

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## MAIN_FRAME

```TypeScript
MAIN_FRAME = 0
```

顶层页面。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## SUB_FRAME

```TypeScript
SUB_FRAME = 1
```

Frame或Iframe。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## STYLE_SHEET

```TypeScript
STYLE_SHEET = 2
```

CSS样式表。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## SCRIPT

```TypeScript
SCRIPT = 3
```

外部脚本。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## IMAGE

```TypeScript
IMAGE = 4
```

图片（jpg/gif/png/以及其他）。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## FONT_RESOURCE

```TypeScript
FONT_RESOURCE = 5
```

字体。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## SUB_RESOURCE

```TypeScript
SUB_RESOURCE = 6
```

其他子资源。如果实际类型未知，则是默认类型。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## OBJECT

```TypeScript
OBJECT = 7
```

插件的Object（或embed）标签，或者插件请求的资源。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## MEDIA

```TypeScript
MEDIA = 8
```

媒体资源。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## WORKER

```TypeScript
WORKER = 9
```

专用工作线程的主资源。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## SHARED_WORKER

```TypeScript
SHARED_WORKER = 10
```

共享工作线程的主资源。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## PREFETCH

```TypeScript
PREFETCH = 11
```

明确的预取请求。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## FAVICON

```TypeScript
FAVICON = 12
```

网站图标。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## XHR

```TypeScript
XHR = 13
```

XMLHttpRequest.

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## PING

```TypeScript
PING = 14
```

<a ping\>/sendBeacon的Ping请求。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## SERVICE_WORKER

```TypeScript
SERVICE_WORKER = 15
```

service worker的主资源。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## CSP_REPORT

```TypeScript
CSP_REPORT = 16
```

内容安全策略违规报告。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## PLUGIN_RESOURCE

```TypeScript
PLUGIN_RESOURCE = 17
```

插件请求的资源。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## NAVIGATION_PRELOAD_MAIN_FRAME

```TypeScript
NAVIGATION_PRELOAD_MAIN_FRAME = 19
```

触发service worker预热的主frame跳转请求。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## NAVIGATION_PRELOAD_SUB_FRAME

```TypeScript
NAVIGATION_PRELOAD_SUB_FRAME = 20
```

触发service worker预热的子frame跳转请求。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

