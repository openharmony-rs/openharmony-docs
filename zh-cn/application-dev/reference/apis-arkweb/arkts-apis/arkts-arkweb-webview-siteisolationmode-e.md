# SiteIsolationMode

站点隔离机制将不同源的网站隔离在不同的渲染子进程中，减少跨域攻击面。例如，PC上原有进程模型是每一个Tab对应一个渲染子进程，站点隔离打开后，让不同源的Iframe运行在独立的渲染子进程中。

**起始版本：** 21

<!--Device-webview-enum SiteIsolationMode--><!--Device-webview-enum SiteIsolationMode-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## PARTIAL

```TypeScript
PARTIAL = 0
```

部分站点隔离，即在同一个渲染进程内加载新站点。

**起始版本：** 21

<!--Device-SiteIsolationMode-PARTIAL = 0--><!--Device-SiteIsolationMode-PARTIAL = 0-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## STRICT

```TypeScript
STRICT = 1
```

严格站点隔离，跨站点的Iframe将切换到新的渲染进程。

**起始版本：** 21

<!--Device-SiteIsolationMode-STRICT = 1--><!--Device-SiteIsolationMode-STRICT = 1-End-->

**系统能力：** SystemCapability.Web.Webview.Core

