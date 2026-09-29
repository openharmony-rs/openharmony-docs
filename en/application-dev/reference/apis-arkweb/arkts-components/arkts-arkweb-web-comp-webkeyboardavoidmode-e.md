# WebKeyboardAvoidMode

```TypeScript
declare enum WebKeyboardAvoidMode
```

Enumerates the soft keyboard avoidance modes.

**Since:** 12

<!--Device-unnamed-declare enum WebKeyboardAvoidMode--><!--Device-unnamed-declare enum WebKeyboardAvoidMode-End-->

**System capability:** SystemCapability.Web.Webview.Core

## RESIZE_VISUAL

```TypeScript
RESIZE_VISUAL = 0
```

For soft keyboard avoidance, the visual viewport is resized, but not the layout viewport.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-WebKeyboardAvoidMode-RESIZE_VISUAL = 0--><!--Device-WebKeyboardAvoidMode-RESIZE_VISUAL = 0-End-->

**System capability:** SystemCapability.Web.Webview.Core

## RESIZE_CONTENT

```TypeScript
RESIZE_CONTENT = 1
```

For soft keyboard avoidance, both the visual viewport and layout viewport are resized. Default value.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-WebKeyboardAvoidMode-RESIZE_CONTENT = 1--><!--Device-WebKeyboardAvoidMode-RESIZE_CONTENT = 1-End-->

**System capability:** SystemCapability.Web.Webview.Core

## OVERLAYS_CONTENT

```TypeScript
OVERLAYS_CONTENT = 2
```

No viewport is resized, and soft keyboard avoidance is not triggered.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-WebKeyboardAvoidMode-OVERLAYS_CONTENT = 2--><!--Device-WebKeyboardAvoidMode-OVERLAYS_CONTENT = 2-End-->

**System capability:** SystemCapability.Web.Webview.Core

## RETURN_TO_UICONTEXT

```TypeScript
RETURN_TO_UICONTEXT = 3
```

The soft keyboard avoidance behavior of the **Web** component follows the [KeyboardAvoidMode](../../apis-arkui/arkts-apis/arkts-arkui-arkui-uicontext-keyboardavoidmode-e.md) set by UIcontext. The **Web** component does not process the avoidance behavior of the component.

**Since:** 22

<!--Device-WebKeyboardAvoidMode-RETURN_TO_UICONTEXT = 3--><!--Device-WebKeyboardAvoidMode-RETURN_TO_UICONTEXT = 3-End-->

**System capability:** SystemCapability.Web.Webview.Core
