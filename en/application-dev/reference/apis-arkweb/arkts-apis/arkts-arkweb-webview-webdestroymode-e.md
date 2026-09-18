# WebDestroyMode

Enumerates the destroy modes of the **Web** component. When the Web component is destroyed, the destroy mode affects the resource release time of the Web kernel, such as the JavaScript running context and rendering context.

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

## NORMAL_MODE

```TypeScript
NORMAL_MODE = 0
```

Normal mode. The system determines the destroy time of **Web** component resources.

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

## FAST_MODE

```TypeScript
FAST_MODE = 1
```

Quick mode. When the **Web** component is destroyed, the related internal resources are destroyed immediately.

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core
