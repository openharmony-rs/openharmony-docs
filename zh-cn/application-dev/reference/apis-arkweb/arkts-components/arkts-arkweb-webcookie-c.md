# WebCookie

通过WebCookie可以控制Web组件中的cookie的各种行为，其中每个应用中的所有Web组件共享一个WebCookie。通过controller方法中的getCookieManager方法可以获取WebCookie对象，进行后续 的cookie管理操作。

**起始版本：** 8

**废弃版本：** 23

**替代接口：** [WebCookieManager](../arkts-apis/arkts-arkweb-webview-webcookiemanager-c.md)

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
```

## constructor

```TypeScript
constructor()
```

WebCookie的构造函数。

**起始版本：** 8

**废弃版本：** 23

**替代接口：** [WebCookieManager](../arkts-apis/arkts-arkweb-webview-webcookiemanager-c.md)

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## saveCookie

```TypeScript
saveCookie()
```

将当前存在内存中的cookie同步到磁盘中，该方法为同步方法。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [saveCookieAsync](../arkts-apis/arkts-arkweb-webview-webcookiemanager-c.md#savecookieasync)

**系统能力：** SystemCapability.Web.Webview.Core

## setCookie

```TypeScript
setCookie()
```

设置cookie，该方法为同步方法。设置成功返回true，否则返回false。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** setCookie

**系统能力：** SystemCapability.Web.Webview.Core
