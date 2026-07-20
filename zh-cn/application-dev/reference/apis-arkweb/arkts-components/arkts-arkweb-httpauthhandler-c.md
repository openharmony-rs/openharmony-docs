# HttpAuthHandler

Defines the http auth request result, related to {@link onHttpAuthRequest} method.

**起始版本：** 9

<!--Device-unnamed-declare class HttpAuthHandler--><!--Device-unnamed-declare class HttpAuthHandler-End-->

**系统能力：** SystemCapability.Web.Webview.Core

<a id="cancel"></a>
## cancel

```TypeScript
cancel(): void
```

通知Web组件用户取消HTTP认证操作。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HttpAuthHandler-cancel(): void--><!--Device-HttpAuthHandler-cancel(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

<a id="confirm"></a>
## confirm

```TypeScript
confirm(userName: string, password: string): boolean
```

使用用户名和密码进行HTTP认证操作。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HttpAuthHandler-confirm(userName: string, password: string): boolean--><!--Device-HttpAuthHandler-confirm(userName: string, password: string): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userName | string | 是 | HTTP认证用户名。 |
| password | string | 是 | HTTP认证密码。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | **true** is returned if the authentication is successful; otherwise, **false** is returned. |

<a id="constructor"></a>
## constructor

```TypeScript
constructor()
```

Constructor.

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HttpAuthHandler-constructor()--><!--Device-HttpAuthHandler-constructor()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

<a id="ishttpauthinfosaved"></a>
## isHttpAuthInfoSaved

```TypeScript
isHttpAuthInfoSaved(): boolean
```

通知Web组件用户使用服务器缓存的账号密码认证。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HttpAuthHandler-isHttpAuthInfoSaved(): boolean--><!--Device-HttpAuthHandler-isHttpAuthInfoSaved(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | **true** is suitable for use; otherwise, **false** is not suitable for use. |

