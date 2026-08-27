# RenderMode

定义Web组件的渲染方式，默认为异步渲染模式。建议使用异步渲染模式，异步渲染模式有更好的性能和更低的功耗。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## ASYNC_RENDER

```TypeScript
ASYNC_RENDER = 0
```

Web组件异步渲染模式，ArkWeb组件作为图形surface节点，独立送显，Web组件的高度最大规格不超过7,680 px（物理像素）。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## SYNC_RENDER

```TypeScript
SYNC_RENDER = 1
```

Web组件同步渲染模式，ArkWeb组件作为图形canvas节点，跟随系统组件一起送显，可以渲染更长的Web组件内容，Web组件的高度最大规格不超过500,000 px（物理像素）。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core
