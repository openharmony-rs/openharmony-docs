# GestureFocusMode

手势获焦的模式。

**起始版本：** 20

<!--Device-unnamed-declare enum GestureFocusMode--><!--Device-unnamed-declare enum GestureFocusMode-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## DEFAULT

```TypeScript
DEFAULT = 0
```

默认值，Web会在触摸按下屏幕时申请获焦，包括点击、长按、滑动、缩放等任何触摸屏幕的手势行为。

**起始版本：** 20

<!--Device-GestureFocusMode-DEFAULT = 0--><!--Device-GestureFocusMode-DEFAULT = 0-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## GESTURE_TAP_AND_LONG_PRESS

```TypeScript
GESTURE_TAP_AND_LONG_PRESS = 1
```

Web只会在点击和长按手势事件生成时申请获焦，点击和长按在触摸抬起之后生成，滑动和缩放等手势行为不会获焦。

**起始版本：** 20

<!--Device-GestureFocusMode-GESTURE_TAP_AND_LONG_PRESS = 1--><!--Device-GestureFocusMode-GESTURE_TAP_AND_LONG_PRESS = 1-End-->

**系统能力：** SystemCapability.Web.Webview.Core

