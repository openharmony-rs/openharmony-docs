# OverScrollMode

设置Web的过滚动模式为关闭或开启。

**起始版本：** 11

<!--Device-unnamed-declare enum OverScrollMode--><!--Device-unnamed-declare enum OverScrollMode-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## NEVER

```TypeScript
NEVER = 0
```

Web过滚动模式关闭。适用于不需要额外滚动效果的页面，如内容高度与容器高度匹配的场景。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-OverScrollMode-NEVER = 0--><!--Device-OverScrollMode-NEVER = 0-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## ALWAYS

```TypeScript
ALWAYS = 1
```

Web过滚动模式开启。适用于需要增强滚动反馈的场景，如列表页面或需要明确滚动边界指示的场景。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-OverScrollMode-ALWAYS = 1--><!--Device-OverScrollMode-ALWAYS = 1-End-->

**系统能力：** SystemCapability.Web.Webview.Core

