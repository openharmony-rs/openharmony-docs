# WebKeyboardAvoidMode

软键盘避让的模式。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## RESIZE_VISUAL

```TypeScript
RESIZE_VISUAL = 0
```

软键盘避让时，仅调整可视视口大小，不调整布局视口大小。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## RESIZE_CONTENT

```TypeScript
RESIZE_CONTENT = 1
```

默认值，软键盘避让时，同时调整可视视口和布局视口的大小。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## OVERLAYS_CONTENT

```TypeScript
OVERLAYS_CONTENT = 2
```

不调整任何视口大小，不会触发软键盘避让。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## RETURN_TO_UICONTEXT

```TypeScript
RETURN_TO_UICONTEXT = 3
```

Web组件的软键盘避让行为将跟随UIcontext设置的[KeyboardAvoidMode](../../apis-arkui/arkts-apis/arkts-arkui-arkui-uicontext-keyboardavoidmode-e.md)模式，Web组件不再处理组件的避让。

**起始版本：** 22

**系统能力：** SystemCapability.Web.Webview.Core
