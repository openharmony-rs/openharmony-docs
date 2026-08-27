# OnFirstContentfulPaintEvent

定义网页首次内容绘制的回调信息，包括加载时间和绘制时间。适用于需要监控页面渲染性能的场景，提升性能优化的准确性和用户体验。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
```

## firstContentfulPaintMs

```TypeScript
firstContentfulPaintMs: number
```

从启动页面加载开始到第一次绘制内容的时间，单位是以毫秒表示。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## navigationStartTick

```TypeScript
navigationStartTick: number
```

启动页面加载开始的时间，单位以微秒表示。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core
