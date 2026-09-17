# BackForwardCacheSupportedFeatures

BackForwardCacheSupportedFeatures is a configuration class in the ArkWeb framework used to selectively allow pages that use specific web features to enter the Back/Forward Cache (BFCache). By default, pages using features such as native embed or media takeover are blocked from entering BFCache, because the browser cannot safely save and restore these complex states bound to system controls. By setting the properties in this class, developers can explicitly allow pages with these features to enter BFCache, but they must manage the lifecycle of the related system controls themselves to avoid resource leaks. For the complete sample code, see [enableBackForwardCache](arkts-arkweb-webview-webviewcontroller-c.md#enablebackforwardcache).

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## Modules to Import

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## constructor

```TypeScript
constructor()
```

Constructs a **BackForwardCacheSupportedFeatures** object.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## mediaTakeOver

```TypeScript
mediaTakeOver: boolean
```

Whether to allow pages using media takeover to enter the back-forward cache.

If allowed, you need to maintain the lifecycle of system controls created for video elements to avoid resource leaks.

true: allowed; false: not allowed.

Default value: false.

**Type:** boolean

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## nativeEmbed

```TypeScript
nativeEmbed: boolean
```

Whether to allow pages using native embed to enter the back-forward cache.

If allowed, you need to maintain the lifecycle of system controls created for native embed elements to avoid resource leaks.

true: allowed; false: not allowed.

Default value: false.

**Type:** boolean

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core
