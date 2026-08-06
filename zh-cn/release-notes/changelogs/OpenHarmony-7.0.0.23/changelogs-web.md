# Web子系统变更说明

## cl.web.1 Cookie存储目录变更

**访问级别**

公共能力

**变更原因**

ArkWeb产生的Cookie目前存储在应用的缓存目录下，清空应用缓存会同时清除Cookie数据，导致Web页面内的登录态丢失。

**变更影响**

此变更涉及应用适配。

变更前：ArkWeb的Cookie存储在应用的缓存目录（/data/storage/el2/base/cache/web/Cookies）下，清空应用缓存（/data/storage/el2/base/cache）会同时清除Cookie数据。

变更后：ArkWeb的Cookie存储在应用的数据目录下，清空应用缓存（/data/storage/el2/base/cache）不会清除Cookie数据。


**起始 API Level**

9

**变更发生版本**

从OpenHarmony SDK 7.0.0.23开始。

**变更的接口/组件**

不涉及

**适配指导**

若应用期望在清空应用缓存时同时清除Cookie，需使用[clearAllCookiesSync<sup>11+</sup>](../../../application-dev/reference/apis-arkweb/arkts-apis-webview-WebCookieManager.md#clearallcookiessync11)、[clearAllCookies<sup>11+</sup>](../../../application-dev/reference/apis-arkweb/arkts-apis-webview-WebCookieManager.md#clearallcookies11)（callback）或[clearAllCookies<sup>11+</sup>](../../../application-dev/reference/apis-arkweb/arkts-apis-webview-WebCookieManager.md#clearallcookies11-1)（Promise）接口清除Cookie。