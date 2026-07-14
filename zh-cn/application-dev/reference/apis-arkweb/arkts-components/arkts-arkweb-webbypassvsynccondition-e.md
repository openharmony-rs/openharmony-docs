# WebBypassVsyncCondition

跳过渲染vsync条件。

**起始版本：** 20

**系统能力：** SystemCapability.Web.Webview.Core

## NONE

```TypeScript
NONE = 0
```

默认值，按vsync调度流程绘制。

**起始版本：** 20

**系统能力：** SystemCapability.Web.Webview.Core

## SCROLLBY_FROM_ZERO_OFFSET

```TypeScript
SCROLLBY_FROM_ZERO_OFFSET = 1
```

在使用scrollby（只支持带滚动偏移量）且Web页面滚动偏移量为0，渲染流程跳过vsync调度直接绘制。

**起始版本：** 20

**系统能力：** SystemCapability.Web.Webview.Core

