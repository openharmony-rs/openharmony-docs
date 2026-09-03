# Class (JsGeolocation)

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @zhang-yinglie-->
<!--Designer: @handyohos-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=fb8a23f8059c1122b20bab74c5aca3cfcd08dbd6 translatedAt=2026-08-07T04:51:37.545Z pushedAt=2026-08-07T08:12:25.548Z -->

JsGeolocation is the authorization response object provided to the app when the Web component receives a web page geolocation permission request. When a web page requests device location information through JavaScript geolocation APIs (such as navigator.geolocation), the app needs to decide whether to authorize the request. Through the invoke method, JsGeolocation allows the app to grant or deny the geolocation permission for web pages of a specified origin, and optionally save the permission decision to the system to avoid repeated authorization prompts when the same origin requests again.

JsGeolocation is applicable to scenarios where web pages in the Web component actively request geolocation permission. The app must first register the [onGeolocationShow event](./arkts-basic-components-web-events.md#ongeolocationshow). When a web page initiates a geolocation permission request, the event callback passes the JsGeolocation object to the app, and the app calls the invoke method in the callback to complete the authorization response. The "ohos.permission.LOCATION" and "ohos.permission.APPROXIMATELY_LOCATION" permissions must also be configured.

> **NOTE**
>
> - The initial APIs of this component are supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 8.
>
> - The sample effect is subject to the actual device.

## constructor

constructor()

Constructor of JsGeolocation. The constructor itself is not directly called by the app. The JsGeolocation instance is typically obtained through the [onGeolocationShow event](./arkts-basic-components-web-events.md#ongeolocationshow) callback.

**System capability**: SystemCapability.Web.Webview.Core

## invoke

invoke(origin: string, allow: boolean, retain: boolean): void

Sets the geolocation permission status of a web page. This method must be called in the [onGeolocationShow event](./arkts-basic-components-web-events.md#ongeolocationshow) callback to respond to the authorization request from the web page that initiated the geolocation permission request.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name   | Type   | Mandatory | Description                                    |
| ------ | ------- | ---- | ---------------------------------------- |
| origin | string | Yes | Web origin that initiates the location permission request, used to identify the source of a geolocation request from a specific website.<br>The origin format must comply with the format defined in RFC 6454. |
| allow  | boolean | Yes  | Geolocation permission status.<br>The value **true** means to enable the geolocation permission, and **false** means the opposite.                            |
| retain | boolean | Yes | Whether to allow the location permission state to be saved to the system. The location permissions saved to the system can be managed through the [GeolocationPermissions](./arkts-apis-webview-GeolocationPermissions.md) API.<br>The value **true** indicates that the location permission state is saved to the system, and **false** indicates that it is not saved to the system. |
<!--no_check-->