# WebResourceType

Enumerates the types of requested resources.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## MAIN_FRAME

```TypeScript
MAIN_FRAME = 0
```

Top-level page.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## SUB_FRAME

```TypeScript
SUB_FRAME = 1
```

Frame or Iframe.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## STYLE_SHEET

```TypeScript
STYLE_SHEET = 2
```

CSS stylesheet.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## SCRIPT

```TypeScript
SCRIPT = 3
```

External script.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## IMAGE

```TypeScript
IMAGE = 4
```

Image (JPG, GIF, PNG, or other format).

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## FONT_RESOURCE

```TypeScript
FONT_RESOURCE = 5
```

Font.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## SUB_RESOURCE

```TypeScript
SUB_RESOURCE = 6
```

Other sub-resource. If the type is unknown, it is used as the default type.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## OBJECT

```TypeScript
OBJECT = 7
```

Object (or embed) tag of the plug-in, or the resource requested by the plug-in.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## MEDIA

```TypeScript
MEDIA = 8
```

Media resource.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## WORKER

```TypeScript
WORKER = 9
```

Main resource of a dedicated worker thread.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## SHARED_WORKER

```TypeScript
SHARED_WORKER = 10
```

Main resource of a shared worker thread.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## PREFETCH

```TypeScript
PREFETCH = 11
```

Explicit prefetch request.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## FAVICON

```TypeScript
FAVICON = 12
```

Website icon.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## XHR

```TypeScript
XHR = 13
```

XMLHttpRequest.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## PING

```TypeScript
PING = 14
```

&lt;a ping&gt;/sendBeacon ping request.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## SERVICE_WORKER

```TypeScript
SERVICE_WORKER = 15
```

Main resource of a service worker.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## CSP_REPORT

```TypeScript
CSP_REPORT = 16
```

Report of Content Security Policy violation.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## PLUGIN_RESOURCE

```TypeScript
PLUGIN_RESOURCE = 17
```

Resource requested by the plug-in.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## NAVIGATION_PRELOAD_MAIN_FRAME

```TypeScript
NAVIGATION_PRELOAD_MAIN_FRAME = 19
```

Main frame redirection request that triggers service worker preloading.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## NAVIGATION_PRELOAD_SUB_FRAME

```TypeScript
NAVIGATION_PRELOAD_SUB_FRAME = 20
```

Subframe redirection request that triggers service worker preloading.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core
