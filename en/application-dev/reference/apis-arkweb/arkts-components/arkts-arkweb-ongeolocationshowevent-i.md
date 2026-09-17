# OnGeolocationShowEvent

Defines the callback information triggered when a request to obtain the geolocation information is received, including the origin information and geolocation object. It is suitable for scenarios where handling geolocation permissions is required.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## geolocation

```TypeScript
geolocation: JsGeolocation
```

User operation.

**Type:** [JsGeolocation](arkts-arkweb-jsgeolocation-c.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## origin

```TypeScript
origin: string
```

Origin of the web page that initiates the geolocation permission request, used to identify the source of the geolocation request from a specific website.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core
