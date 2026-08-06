# ScrollbarMode

Enum type supplied to \_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ for indicating the web component scrollbar mode.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-webview-enum ScrollbarMode--><!--Device-webview-enum ScrollbarMode-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## OVERLAY_LAYOUT_SCROLLBAR

```TypeScript
OVERLAY_LAYOUT_SCROLLBAR = 0
```

The normal scrollbar mode, A scrollbar suspended above the content, appearing when scrolling and automatically hiding when stationary. Draw using layout viewport, which can be dragged and dropped.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-ScrollbarMode-OVERLAY_LAYOUT_SCROLLBAR = 0--><!--Device-ScrollbarMode-OVERLAY_LAYOUT_SCROLLBAR = 0-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## FORCE_DISPLAY_SCROLLBAR

```TypeScript
FORCE_DISPLAY_SCROLLBAR = 1
```

The Resident scrollbar mode, Always display a fixed position scrollbar in the content area.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-ScrollbarMode-FORCE_DISPLAY_SCROLLBAR = 1--><!--Device-ScrollbarMode-FORCE_DISPLAY_SCROLLBAR = 1-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## OVERLAY_VISUAL_SCROLLBAR

```TypeScript
OVERLAY_VISUAL_SCROLLBAR = 2
```

Overlay VisualViewport scrollbars: appear on scroll, hide when idle. Rendered via Visual Viewport, non-draggable.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ScrollbarMode-OVERLAY_VISUAL_SCROLLBAR = 2--><!--Device-ScrollbarMode-OVERLAY_VISUAL_SCROLLBAR = 2-End-->

**系统能力：** SystemCapability.Web.Webview.Core

