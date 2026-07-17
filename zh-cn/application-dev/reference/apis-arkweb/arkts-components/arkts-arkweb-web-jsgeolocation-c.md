# JsGeolocation

Defines the js geolocation request.

**起始版本：** 8

<!--Device-unnamed-declare class JsGeolocation--><!--Device-unnamed-declare class JsGeolocation-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## constructor

```TypeScript
constructor()
```

Constructor.

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-JsGeolocation-constructor()--><!--Device-JsGeolocation-constructor()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## invoke

```TypeScript
invoke(origin: string, allow: boolean, retain: boolean): void
```

Report the geolocation permission status from users.

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-JsGeolocation-invoke(origin: string, allow: boolean, retain: boolean): void--><!--Device-JsGeolocation-invoke(origin: string, allow: boolean, retain: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| origin | string | 是 | Index of the origin. |
| allow | boolean | 是 | Geolocation permission status. {@code true} means to allow geolocation permission;{@code false} means to disallow geolocation permission. |
| retain | boolean | 是 | Whether the geolocation permission status can be saved to the system.{@code true} means to allow the geolocation permission status to be saved to the system; {@code false} means to disallow the geolocation permission status to be saved to the system. You can manage the geolocation permissions saved to the system through {@link GeolocationPermissions}. |

