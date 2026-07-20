# WebKeyboardAvoidMode

Enum type supplied to {@link keyboardAvoidMode} for setting the web keyboard avoid mode.

**起始版本：** 12

<!--Device-unnamed-declare enum WebKeyboardAvoidMode--><!--Device-unnamed-declare enum WebKeyboardAvoidMode-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## RESIZE_VISUAL

```TypeScript
RESIZE_VISUAL = 0
```

Resize the visual viewport when keyboard avoidance occurs.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebKeyboardAvoidMode-RESIZE_VISUAL = 0--><!--Device-WebKeyboardAvoidMode-RESIZE_VISUAL = 0-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## RESIZE_CONTENT

```TypeScript
RESIZE_CONTENT = 1
```

Resize the visual and layout viewport when keyboard avoidance occurs.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebKeyboardAvoidMode-RESIZE_CONTENT = 1--><!--Device-WebKeyboardAvoidMode-RESIZE_CONTENT = 1-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## OVERLAYS_CONTENT

```TypeScript
OVERLAYS_CONTENT = 2
```

Do not resize any viewport when keyboard avoidance occurs.

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WebKeyboardAvoidMode-OVERLAYS_CONTENT = 2--><!--Device-WebKeyboardAvoidMode-OVERLAYS_CONTENT = 2-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## RETURN_TO_UICONTEXT

```TypeScript
RETURN_TO_UICONTEXT = 3
```

When the soft keyboard avoids, follow the avoid result of UIContext.

**起始版本：** 22

<!--Device-WebKeyboardAvoidMode-RETURN_TO_UICONTEXT = 3--><!--Device-WebKeyboardAvoidMode-RETURN_TO_UICONTEXT = 3-End-->

**系统能力：** SystemCapability.Web.Webview.Core

