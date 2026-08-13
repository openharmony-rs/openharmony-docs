# WebKeyboardAvoidMode

Enum type supplied to keyboardAvoidMode for setting the web keyboard avoid mode.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare enum WebKeyboardAvoidMode--><!--Device-unnamed-export declare enum WebKeyboardAvoidMode-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## RESIZE_VISUAL

```TypeScript
RESIZE_VISUAL = 0
```

When the soft keyboard avoids, only the size of the visual viewport is adjusted, not the size of the layout viewport.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebKeyboardAvoidMode-RESIZE_VISUAL = 0--><!--Device-WebKeyboardAvoidMode-RESIZE_VISUAL = 0-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## RESIZE_CONTENT

```TypeScript
RESIZE_CONTENT = 1
```

By default, when the soft keyboard avoids, the sizes of the visual viewport and the layout viewport are adjusted at the same time.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebKeyboardAvoidMode-RESIZE_CONTENT = 1--><!--Device-WebKeyboardAvoidMode-RESIZE_CONTENT = 1-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## OVERLAYS_CONTENT

```TypeScript
OVERLAYS_CONTENT = 2
```

Without adjusting any viewport size, soft keyboard avoidance will not be triggered.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebKeyboardAvoidMode-OVERLAYS_CONTENT = 2--><!--Device-WebKeyboardAvoidMode-OVERLAYS_CONTENT = 2-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## RETURN_TO_UICONTEXT

```TypeScript
RETURN_TO_UICONTEXT = 3
```

When the soft keyboard avoid, follow the avoid result of UIContext.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-WebKeyboardAvoidMode-RETURN_TO_UICONTEXT = 3--><!--Device-WebKeyboardAvoidMode-RETURN_TO_UICONTEXT = 3-End-->

**系统能力：** SystemCapability.Web.Webview.Core

