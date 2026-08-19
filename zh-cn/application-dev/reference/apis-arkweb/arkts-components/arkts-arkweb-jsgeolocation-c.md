# JsGeolocation

JsGeolocation是Web组件在收到网页地理位置权限请求时，提供给应用的授权响应对象。当网页通过JavaScript调用地理位置接口（如navigator.geolocation）请求获取设备位置信息时，应用需要决定是否授权该 请求。JsGeolocation通过invoke方法允许应用对指定源的网页授予或拒绝地理位置权限，同时可选择将该权限决策保存到系统中，避免后续同一源再次请求时重复弹出授权提示。 JsGeolocation适用于Web组件中网页主动请求地理位置权限的场景。应用需先注册[onGeolocationShow事件](arkts-arkweb-web-attribute.md#ongeolocationshow)，当网页发起地理位置权限请求 时，该事件回调会将JsGeolocation对象传递给应用，应用在回调中调用invoke方法完成授权响应。使用时还需配置"ohos.permission.LOCATION"、" ohos.permission.APPROXIMATELY_LOCATION"权限。

**起始版本：** 8

<!--Device-unnamed-declare class JsGeolocation--><!--Device-unnamed-declare class JsGeolocation-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { WebNetErrorList } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { webview } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionContext } from '@kit.ArkWeb';
```

## constructor

```TypeScript
constructor()
```

JsGeolocation的构造函数。构造函数本身不直接被应用调用，通常通过[onGeolocationShow事件](arkts-arkweb-web-attribute.md#ongeolocationshow)回调获取JsGeolocation实 例。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-JsGeolocation-constructor()--><!--Device-JsGeolocation-constructor()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## invoke

```TypeScript
invoke(origin: string, allow: boolean, retain: boolean): void
```

设置网页地理位置权限状态。该方法需在[onGeolocationShow事件](arkts-arkweb-web-attribute.md#ongeolocationshow)回调中调用，用于对发起地理位置权限请求的网页进行授权响应。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-JsGeolocation-invoke(origin: string, allow: boolean, retain: boolean): void--><!--Device-JsGeolocation-invoke(origin: string, allow: boolean, retain: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| origin | string | 是 | 发起地理位置权限请求的网页源，用于标识特定网站的地理位置请求来源。 <br>origin格式必须遵循RFC 6454中定义的格式。 |
| allow | boolean | 是 | 设置的地理位置权限状态。 <br>true表示开启地理位置权限，false表示不开启地理位置权限。 |
| retain | boolean | 是 | 是否允许将地理位置权限状态保存到系统中。可通过 [GeolocationPermissions](../arkts-apis/arkts-arkweb-webview-geolocationpermissions-c.md)接口管理保存到系统的地理位置权限。 <br>true表示保存地理位置权限状态到系统，false表示不保存到系统。 |

