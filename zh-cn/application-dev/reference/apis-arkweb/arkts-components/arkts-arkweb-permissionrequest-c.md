# PermissionRequest

权限请求。

**起始版本：** 9

<!--Device-unnamed-declare class PermissionRequest--><!--Device-unnamed-declare class PermissionRequest-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## constructor

```TypeScript
constructor()
```

PermissionRequest的构造函数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PermissionRequest-constructor()--><!--Device-PermissionRequest-constructor()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## deny

```TypeScript
deny(): void
```

Reject the request.

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PermissionRequest-deny(): void--><!--Device-PermissionRequest-deny(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## getAccessibleResource

```TypeScript
getAccessibleResource(): Array<string>
```

Gets the resource that the webpage is trying to access.

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PermissionRequest-getAccessibleResource(): Array<string>--><!--Device-PermissionRequest-getAccessibleResource(): Array<string>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | @syscap SystemCapability.Web.Webview.Core@crossplatform |

## getOrigin

```TypeScript
getOrigin(): string
```

Gets the source if the webpage that attempted to access the restricted resource.

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PermissionRequest-getOrigin(): string--><!--Device-PermissionRequest-getOrigin(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | @syscap SystemCapability.Web.Webview.Core@crossplatform |

## grant

```TypeScript
grant(resources: Array<string>): void
```

Grant origin access to a given resource.

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PermissionRequest-grant(resources: Array<string>): void--><!--Device-PermissionRequest-grant(resources: Array<string>): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resources | Array&lt;string&gt; | 是 | List of resources that can be requested by the web page with the permission to |

