# ViewportFit

网页meta中viewport-fit配置的视口类型。

**起始版本：** 12

<!--Device-unnamed-declare enum ViewportFit--><!--Device-unnamed-declare enum ViewportFit-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## AUTO

```TypeScript
AUTO = 0
```

默认值，整个网页可见。适用于希望网页完全在可视区域内显示的场景，推荐用于大多数常规网页。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ViewportFit-AUTO = 0--><!--Device-ViewportFit-AUTO = 0-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## CONTAINS

```TypeScript
CONTAINS = 1
```

初始布局视口和视觉视口为适应设备显示屏的最大矩形内。适用于需要确保内容完全在安全区域内的场景，如避免刘海屏遮挡重要内容。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ViewportFit-CONTAINS = 1--><!--Device-ViewportFit-CONTAINS = 1-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## COVER

```TypeScript
COVER = 2
```

初始布局视口和视觉视口为设备物理屏幕的外接矩形内。适用于需要网页内容延伸到屏幕边缘的场景，如全屏背景效果或沉浸式体验。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ViewportFit-COVER = 2--><!--Device-ViewportFit-COVER = 2-End-->

**系统能力：** SystemCapability.Web.Webview.Core

