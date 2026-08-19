# WebSoftKeyboardBehaviorMode

Web软键盘自动控制模式。

**起始版本：** 22

<!--Device-webview-enum WebSoftKeyboardBehaviorMode--><!--Device-webview-enum WebSoftKeyboardBehaviorMode-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## DEFAULT

```TypeScript
DEFAULT = 0
```

当Web组件失去焦点或获得焦点、状态切换为inactive或active时，系统均会尝试触发软键盘自动隐藏或拉起（默认值）。

**起始版本：** 22

<!--Device-WebSoftKeyboardBehaviorMode-DEFAULT = 0--><!--Device-WebSoftKeyboardBehaviorMode-DEFAULT = 0-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## DISABLE_AUTO_KEYBOARD_ON_ACTIVE

```TypeScript
DISABLE_AUTO_KEYBOARD_ON_ACTIVE = 1
```

Web组件在inactive或active状态切换时，系统不再尝试触发软键盘自动隐藏或拉起。

**起始版本：** 22

<!--Device-WebSoftKeyboardBehaviorMode-DISABLE_AUTO_KEYBOARD_ON_ACTIVE = 1--><!--Device-WebSoftKeyboardBehaviorMode-DISABLE_AUTO_KEYBOARD_ON_ACTIVE = 1-End-->

**系统能力：** SystemCapability.Web.Webview.Core

