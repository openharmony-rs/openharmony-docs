# WebSoftKeyboardBehaviorMode

```TypeScript
enum WebSoftKeyboardBehaviorMode
```

Enumerates the behavior modes of the web soft keyboard.

**Since:** 22

<!--Device-webview-enum WebSoftKeyboardBehaviorMode--><!--Device-webview-enum WebSoftKeyboardBehaviorMode-End-->

**System capability:** SystemCapability.Web.Webview.Core

## DEFAULT

```TypeScript
DEFAULT = 0
```

When the **Web** component is focused or unfocused, or its status changes to inactive or active, the system attempts to hide or display the soft keyboard. This value is used by default.

**Since:** 22

<!--Device-WebSoftKeyboardBehaviorMode-DEFAULT = 0--><!--Device-WebSoftKeyboardBehaviorMode-DEFAULT = 0-End-->

**System capability:** SystemCapability.Web.Webview.Core

## DISABLE_AUTO_KEYBOARD_ON_ACTIVE

```TypeScript
DISABLE_AUTO_KEYBOARD_ON_ACTIVE = 1
```

When the **Web** component's status changes between inactive and active, the system does not hide or start the soft keyboard.

**Since:** 22

<!--Device-WebSoftKeyboardBehaviorMode-DISABLE_AUTO_KEYBOARD_ON_ACTIVE = 1--><!--Device-WebSoftKeyboardBehaviorMode-DISABLE_AUTO_KEYBOARD_ON_ACTIVE = 1-End-->

**System capability:** SystemCapability.Web.Webview.Core
