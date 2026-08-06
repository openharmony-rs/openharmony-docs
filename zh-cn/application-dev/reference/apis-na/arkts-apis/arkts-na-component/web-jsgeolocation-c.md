# JsGeolocation

Defines the js geolocation request.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class JsGeolocation--><!--Device-unnamed-export declare class JsGeolocation-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## constructor

```TypeScript
constructor()
```

Constructor.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-JsGeolocation-constructor()--><!--Device-JsGeolocation-constructor()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## invoke

```TypeScript
invoke(origin: string, allow: boolean, retain: boolean): void
```

Sets the geolocation permission status of a web page.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-JsGeolocation-invoke(origin: string, allow: boolean, retain: boolean): void--><!--Device-JsGeolocation-invoke(origin: string, allow: boolean, retain: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| origin | string | 是 | Index of the origin. |
| allow | boolean | 是 | Geolocation permission status. {@code true} means to allow geolocation permission;{@code false} means to disallow geolocation permission. |
| retain | boolean | 是 | Whether the geolocation permission status can be saved to the system.{@code true} means to allow the geolocation permission status to be saved to the system; {@code false} means to disallow the geolocation permission status to be saved to the system. You can manage the geolocation permissions saved to the system through \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_. |

