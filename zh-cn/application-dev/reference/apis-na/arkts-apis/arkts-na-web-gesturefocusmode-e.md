# GestureFocusMode

Enum type supplied to gestureFocusMode for setting the web gesture focus mode.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare enum GestureFocusMode--><!--Device-unnamed-export declare enum GestureFocusMode-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## DEFAULT

```TypeScript
DEFAULT = 0
```

Any action on a web component, such as tapping, long-pressing, scrolling, zooming, etc., will cause the web component to acquire focus on touch down.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-GestureFocusMode-DEFAULT = 0--><!--Device-GestureFocusMode-DEFAULT = 0-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## GESTURE_TAP_AND_LONG_PRESS

```TypeScript
GESTURE_TAP_AND_LONG_PRESS = 1
```

Tap and long-press gestures will cause the web component to acquire focus after touch up, while gestures such as scrolling, zooming, etc., do not request focus.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-GestureFocusMode-GESTURE_TAP_AND_LONG_PRESS = 1--><!--Device-GestureFocusMode-GESTURE_TAP_AND_LONG_PRESS = 1-End-->

**系统能力：** SystemCapability.Web.Webview.Core

