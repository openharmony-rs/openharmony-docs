# WebResourceType

Defines the resource type of request.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-webview-enum WebResourceType--><!--Device-webview-enum WebResourceType-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## MAIN_FRAME

```TypeScript
MAIN_FRAME = 0
```

Top level page.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-WebResourceType-MAIN_FRAME = 0--><!--Device-WebResourceType-MAIN_FRAME = 0-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## SUB_FRAME

```TypeScript
SUB_FRAME = 1
```

Frame or Iframe.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-WebResourceType-SUB_FRAME = 1--><!--Device-WebResourceType-SUB_FRAME = 1-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## STYLE_SHEET

```TypeScript
STYLE_SHEET = 2
```

CSS stylesheet.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-WebResourceType-STYLE_SHEET = 2--><!--Device-WebResourceType-STYLE_SHEET = 2-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## SCRIPT

```TypeScript
SCRIPT = 3
```

External script.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-WebResourceType-SCRIPT = 3--><!--Device-WebResourceType-SCRIPT = 3-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## IMAGE

```TypeScript
IMAGE = 4
```

Image (jpg/gif/png/etc).

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-WebResourceType-IMAGE = 4--><!--Device-WebResourceType-IMAGE = 4-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## FONT_RESOURCE

```TypeScript
FONT_RESOURCE = 5
```

Font.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-WebResourceType-FONT_RESOURCE = 5--><!--Device-WebResourceType-FONT_RESOURCE = 5-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## SUB_RESOURCE

```TypeScript
SUB_RESOURCE = 6
```

Some other subresource. This is the default type if the actual type is unknown.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-WebResourceType-SUB_RESOURCE = 6--><!--Device-WebResourceType-SUB_RESOURCE = 6-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## OBJECT

```TypeScript
OBJECT = 7
```

Object (or embed) tag for a plugin, or a resource that a plugin requested.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-WebResourceType-OBJECT = 7--><!--Device-WebResourceType-OBJECT = 7-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## MEDIA

```TypeScript
MEDIA = 8
```

Media resource.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-WebResourceType-MEDIA = 8--><!--Device-WebResourceType-MEDIA = 8-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## WORKER

```TypeScript
WORKER = 9
```

Main resource of a dedicated worker.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-WebResourceType-WORKER = 9--><!--Device-WebResourceType-WORKER = 9-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## SHARED_WORKER

```TypeScript
SHARED_WORKER = 10
```

Main resource of a shared worker.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-WebResourceType-SHARED_WORKER = 10--><!--Device-WebResourceType-SHARED_WORKER = 10-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## PREFETCH

```TypeScript
PREFETCH = 11
```

Explicitly requested prefetch.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-WebResourceType-PREFETCH = 11--><!--Device-WebResourceType-PREFETCH = 11-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## FAVICON

```TypeScript
FAVICON = 12
```

Favicon.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-WebResourceType-FAVICON = 12--><!--Device-WebResourceType-FAVICON = 12-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## XHR

```TypeScript
XHR = 13
```

XMLHttpRequest.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-WebResourceType-XHR = 13--><!--Device-WebResourceType-XHR = 13-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## PING

```TypeScript
PING = 14
```

Ping request for &lt;a ping&gt;/sendBeacon.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-WebResourceType-PING = 14--><!--Device-WebResourceType-PING = 14-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## SERVICE_WORKER

```TypeScript
SERVICE_WORKER = 15
```

The main resource of a service worker.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-WebResourceType-SERVICE_WORKER = 15--><!--Device-WebResourceType-SERVICE_WORKER = 15-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## CSP_REPORT

```TypeScript
CSP_REPORT = 16
```

Report of Content Security Policy violations.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-WebResourceType-CSP_REPORT = 16--><!--Device-WebResourceType-CSP_REPORT = 16-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## PLUGIN_RESOURCE

```TypeScript
PLUGIN_RESOURCE = 17
```

Resource that a plugin requested.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-WebResourceType-PLUGIN_RESOURCE = 17--><!--Device-WebResourceType-PLUGIN_RESOURCE = 17-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## NAVIGATION_PRELOAD_MAIN_FRAME

```TypeScript
NAVIGATION_PRELOAD_MAIN_FRAME = 19
```

A main-frame service worker navigation preload request.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-WebResourceType-NAVIGATION_PRELOAD_MAIN_FRAME = 19--><!--Device-WebResourceType-NAVIGATION_PRELOAD_MAIN_FRAME = 19-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## NAVIGATION_PRELOAD_SUB_FRAME

```TypeScript
NAVIGATION_PRELOAD_SUB_FRAME = 20
```

A sub-frame service worker navigation preload request.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-WebResourceType-NAVIGATION_PRELOAD_SUB_FRAME = 20--><!--Device-WebResourceType-NAVIGATION_PRELOAD_SUB_FRAME = 20-End-->

**系统能力：** SystemCapability.Web.Webview.Core

