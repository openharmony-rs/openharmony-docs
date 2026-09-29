# CacheOptions

```TypeScript
interface CacheOptions
```

Represents a configuration object for precompiling JavaScript in the **Web** component to generate bytecode cache, which is designed to control the updating of the bytecode cache.

**Since:** 12

<!--Device-webview-interface CacheOptions--><!--Device-webview-interface CacheOptions-End-->

**System capability:** SystemCapability.Web.Webview.Core

## Modules to Import

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## responseHeaders

```TypeScript
responseHeaders: Array<WebHeader>
```

Response headers returned by the server when requesting this JavaScript file. ETag or Last-Modified is used to identify the file version and determine whether an update is needed.

**Type:** Array&lt;[WebHeader](arkts-arkweb-webview-webheader-i.md)&gt;

**Since:** 12

<!--Device-CacheOptions-responseHeaders: Array<WebHeader>--><!--Device-CacheOptions-responseHeaders: Array<WebHeader>-End-->

**System capability:** SystemCapability.Web.Webview.Core
