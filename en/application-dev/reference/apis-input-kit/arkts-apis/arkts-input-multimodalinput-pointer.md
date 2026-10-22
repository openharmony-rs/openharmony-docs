# @ohos.multimodalInput.pointer(Mouse Pointer and pointer-type external devices)

This module provides management of the mouse cursor and cursor type external devices, and is used to query and set the related attributes of the mouse cursor and cursor type external devices.

**Since:** 9

<!--Device-unnamed-declare namespace pointer--><!--Device-unnamed-declare namespace pointer-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Pointer

## Modules to Import

```TypeScript
import { pointer } from '@kit.InputKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getPointerStyle](arkts-input-pointer-getpointerstyle-f.md#getpointerstyle-1) | Obtains the mouse pointer style type of a specified window. This API can obtain only the mouse pointer style type of windows within the current application process. This API uses an asynchronous callback to return the result. |
| [getPointerStyle](arkts-input-pointer-getpointerstyle-f.md#getpointerstyle-2) | Obtains the mouse pointer style type. This API can obtain only the mouse pointer style type of windows within the current application process. This API uses a promise to return the result. |
| [getPointerStyleSync](arkts-input-pointer-getpointerstylesync-f.md#getpointerstylesync-1) | Queries the mouse pointer style type of a specified window, such as east arrow, west arrow, south arrow, and north arrow. This API can obtain only the mouse pointer style type of windows within the current application process. |
| [getTouchpadScrollDirection](arkts-input-pointer-gettouchpadscrolldirection-f.md#gettouchpadscrolldirection-1) | Obtains the touchpad scroll direction. This API uses an asynchronous callback to return the result. |
| [getTouchpadScrollDirection](arkts-input-pointer-gettouchpadscrolldirection-f.md#gettouchpadscrolldirection-2) | Obtains the scroll direction of the touchpad. This API uses a promise to return the result. |
| [isPointerVisible](arkts-input-pointer-ispointervisible-f.md#ispointervisible-1) | Obtains the display/hidden state of the current window. This state reflects the cursor display/hidden state of the multimodal process for the process where the window resides, not the actual cursor display/hidden status. Whether the cursor is correctly displayed/hidden is also affected by the render service process. This API uses an asynchronous callback to return the result. |
| [isPointerVisible](arkts-input-pointer-ispointervisible-f.md#ispointervisible-2) | Obtains the display/hidden state of the current window. This state reflects the cursor display/hidden state of the multimodal process for the process where the window resides, not the actual cursor display/hidden status. Whether the cursor is correctly displayed/hidden is also affected by the render service process. This API uses a promise to return the result. |
| [isPointerVisibleSync](arkts-input-pointer-ispointervisiblesync-f.md#ispointervisiblesync-1) | Obtains the display/hidden state of the current window. This state reflects the cursor display/hidden state of the multimodal process for the process where the window resides, not the actual cursor display/hidden status. Whether the cursor is correctly displayed/hidden is also affected by the render service process. This API is called synchronously. |
| [setCustomCursor](arkts-input-pointer-setcustomcursor-f.md#setcustomcursor-1) | Sets a custom pointer style for a specified window. This API can set only the custom pointer style of windows within the current application process. For details about how to set the custom pointer style of the host window through the **UIExtensionAbility** process, see [setCustomCursor](../../apis-arkui/arkts-apis/arkts-arkui-arkui-uicontext-cursorcontroller-c.md#setcustomcursor). This API uses a promise to return the result. |
| [setCustomCursor](arkts-input-pointer-setcustomcursor-f.md#setcustomcursor-2) | Sets a custom pointer style for a specified window. This API can set only the custom pointer style of windows within the current application process. For details about how to set the custom pointer style of the host window through the **UIExtensionAbility** process, see [setCustomCursor](../../apis-arkui/arkts-apis/arkts-arkui-arkui-uicontext-cursorcontroller-c.md#setcustomcursor). This API uses a promise to return the result. |
| [setCustomCursorSync](arkts-input-pointer-setcustomcursorsync-f.md#setcustomcursorsync-1) | Sets a custom pointer style for a specified window synchronously. This API can set only the custom pointer style of windows within the current application process. For details about how to set the custom pointer style of the host window through the **UIExtensionAbility** process, see [setCustomCursor](../../apis-arkui/arkts-apis/arkts-arkui-arkui-uicontext-cursorcontroller-c.md#setcustomcursor). |
| [setPointerStyle](arkts-input-pointer-setpointerstyle-f.md#setpointerstyle-1) | Sets the mouse pointer style type for a specified window. This API can set only the mouse pointer style type of windows within the current application process. For details about how to set the mouse pointer style type of the host window through the **UIExtensionAbility** process, see [setCursor](../../apis-arkui/arkts-apis/arkts-arkui-arkui-uicontext-cursorcontroller-c.md#setcursor). This API uses an asynchronous callback to return the result. |
| [setPointerStyle](arkts-input-pointer-setpointerstyle-f.md#setpointerstyle-2) | Sets the mouse pointer style type for a specified window. This API can set only the mouse pointer style type of windows within the current application process. For details about how to set the mouse pointer style type of the host window through the **UIExtensionAbility** process, see [setCursor](../../apis-arkui/arkts-apis/arkts-arkui-arkui-uicontext-cursorcontroller-c.md#setcursor). This uses a promise to return the result. |
| [setPointerStyleSync](arkts-input-pointer-setpointerstylesync-f.md#setpointerstylesync-1) | Sets the mouse pointer style type for a specified window and returns the result synchronously. This API can set only the mouse pointer style type of windows within the current application process. For details about how to set the mouse pointer style type of the host window through the **UIExtensionAbility** process, see [setCursor](../../apis-arkui/arkts-apis/arkts-arkui-arkui-uicontext-cursorcontroller-c.md#setcursor). |
| [setPointerVisible](arkts-input-pointer-setpointervisible-f.md#setpointervisible-1) | Sets the cursor display/hidden state. This state applies to all windows of the current process. The actual display/hidden effect of the cursor on the screen is also affected by the render service process. This API uses an asynchronous callback to return the result. |
| [setPointerVisible](arkts-input-pointer-setpointervisible-f.md#setpointervisible-2) | Sets the cursor display/hidden state. This state applies to all windows of the current process. The actual display/hidden effect of the cursor on the screen is also affected by the render service process. This API uses a promise to return the result. |
| [setPointerVisibleSync](arkts-input-pointer-setpointervisiblesync-f.md#setpointervisiblesync-1) | Sets the cursor display/hidden state. This state applies to all windows of the current process. The actual display/hidden effect of the cursor on the screen is also affected by the render service process. This API is called synchronously. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getHoverScrollState](arkts-input-pointer-gethoverscrollstate-f-sys.md#gethoverscrollstate-1) | Obtains the mouse hover scrolling switch state. This API uses an asynchronous callback to return the result. |
| [getHoverScrollState](arkts-input-pointer-gethoverscrollstate-f-sys.md#gethoverscrollstate-2) | Obtains the status of the mouse hover scroll switch. This API uses a promise to return the result. |
| [getMousePrimaryButton](arkts-input-pointer-getmouseprimarybutton-f-sys.md#getmouseprimarybutton-1) | Obtains the current primary mouse button. This API uses an asynchronous callback to return the result. |
| [getMousePrimaryButton](arkts-input-pointer-getmouseprimarybutton-f-sys.md#getmouseprimarybutton-2) | Obtains the current primary mouse button. This API uses a promise to return the result. |
| [getMouseScrollDirection](arkts-input-pointer-getmousescrolldirection-f-sys.md#getmousescrolldirection-1) | Obtains the scroll direction of the mouse wheel. This API uses a promise to return the result asynchronously. |
| [getMouseScrollRows](arkts-input-pointer-getmousescrollrows-f-sys.md#getmousescrollrows-1) | Obtains the number of mouse scroll lines. This API uses an asynchronous callback to return the result. |
| [getMouseScrollRows](arkts-input-pointer-getmousescrollrows-f-sys.md#getmousescrollrows-2) | Obtains the number of mouse scroll lines. This API uses a promise to return the result. |
| [getPointerColor](arkts-input-pointer-getpointercolor-f-sys.md#getpointercolor-1) | Obtains the mouse pointer color. This API uses an asynchronous callback to return the result. |
| [getPointerColor](arkts-input-pointer-getpointercolor-f-sys.md#getpointercolor-2) | Obtains the current mouse pointer color. This API uses a promise to return the result. |
| [getPointerColorSync](arkts-input-pointer-getpointercolorsync-f-sys.md#getpointercolorsync-1) | Obtains the pointer color. This API returns the result synchronously. |
| [getPointerSize](arkts-input-pointer-getpointersize-f-sys.md#getpointersize-1) | Obtains the current mouse pointer size. This API uses an asynchronous callback to return the result. |
| [getPointerSize](arkts-input-pointer-getpointersize-f-sys.md#getpointersize-2) | Obtains the current mouse pointer size. This API uses a promise to return the result. |
| [getPointerSizeSync](arkts-input-pointer-getpointersizesync-f-sys.md#getpointersizesync-1) | Obtains the pointer size. This API returns the result synchronously. |
| [getPointerSpeed](arkts-input-pointer-getpointerspeed-f-sys.md#getpointerspeed-1) | Obtains the mouse pointer speed. This API uses an asynchronous callback to return the result. |
| [getPointerSpeed](arkts-input-pointer-getpointerspeed-f-sys.md#getpointerspeed-2) | Obtains the mouse pointer speed. This API uses a promise to return the result. |
| [getPointerSpeedSync](arkts-input-pointer-getpointerspeedsync-f-sys.md#getpointerspeedsync-1) | Obtains the mouse pointer speed. This API returns the result synchronously. |
| [getTouchpadDoubleTapAndDragState](arkts-input-pointer-gettouchpaddoubletapanddragstate-f-sys.md#gettouchpaddoubletapanddragstate-1) | Obtains the touchpad double-tap and drag switch state. This API uses an asynchronous callback to return the result. |
| [getTouchpadDoubleTapAndDragState](arkts-input-pointer-gettouchpaddoubletapanddragstate-f-sys.md#gettouchpaddoubletapanddragstate-2) | Obtains the touchpad double-tap and drag switch state. This API uses a promise to return the result. |
| [getTouchpadPinchSwitch](arkts-input-pointer-gettouchpadpinchswitch-f-sys.md#gettouchpadpinchswitch-1) | Obtains the touchpad pinch switch state. This API uses an asynchronous callback to return the result. |
| [getTouchpadPinchSwitch](arkts-input-pointer-gettouchpadpinchswitch-f-sys.md#gettouchpadpinchswitch-2) | Obtains the touchpad pinch switch state. This API uses a promise to return the result. |
| [getTouchpadPointerSpeed](arkts-input-pointer-gettouchpadpointerspeed-f-sys.md#gettouchpadpointerspeed-1) | Obtains the touchpad pointer speed. This API uses an asynchronous callback to return the result. |
| [getTouchpadPointerSpeed](arkts-input-pointer-gettouchpadpointerspeed-f-sys.md#gettouchpadpointerspeed-2) | Obtains the touchpad pointer speed. This API uses a promise to return the result. |
| [getTouchpadRightClickType](arkts-input-pointer-gettouchpadrightclicktype-f-sys.md#gettouchpadrightclicktype-1) | Obtains the touchpad right-click menu type. This API uses an asynchronous callback to return the result. |
| [getTouchpadRightClickType](arkts-input-pointer-gettouchpadrightclicktype-f-sys.md#gettouchpadrightclicktype-2) | Obtains the touchpad right-click menu type. This API uses a promise to return the result. |
| [getTouchpadScrollSwitch](arkts-input-pointer-gettouchpadscrollswitch-f-sys.md#gettouchpadscrollswitch-1) | Obtains the touchpad scroll switch state. This API uses an asynchronous callback to return the result. |
| [getTouchpadScrollSwitch](arkts-input-pointer-gettouchpadscrollswitch-f-sys.md#gettouchpadscrollswitch-2) | Obtains the touchpad scroll switch state. This API uses a promise to return the result. |
| [getTouchpadSwipeSwitch](arkts-input-pointer-gettouchpadswipeswitch-f-sys.md#gettouchpadswipeswitch-1) | Obtains the touchpad multi-finger swipe switch state. This API uses an asynchronous callback to return the result. |
| [getTouchpadSwipeSwitch](arkts-input-pointer-gettouchpadswipeswitch-f-sys.md#gettouchpadswipeswitch-2) | Obtains the touchpad multi-finger swipe switch state. This API uses a promise to return the result. |
| [getTouchpadTapSwitch](arkts-input-pointer-gettouchpadtapswitch-f-sys.md#gettouchpadtapswitch-1) | Obtains the touchpad tap switch state. This API uses an asynchronous callback to return the result. |
| [getTouchpadTapSwitch](arkts-input-pointer-gettouchpadtapswitch-f-sys.md#gettouchpadtapswitch-2) | Obtains the touchpad tap switch state. This API uses a promise to return the result. |
| [setHoverScrollState](arkts-input-pointer-sethoverscrollstate-f-sys.md#sethoverscrollstate-1) | Sets the mouse hover scrolling switch state. This API uses an asynchronous callback to return the result. |
| [setHoverScrollState](arkts-input-pointer-sethoverscrollstate-f-sys.md#sethoverscrollstate-2) | Sets the status of the mouse hover scroll switch. This API uses a promise to return the result. |
| [setMousePrimaryButton](arkts-input-pointer-setmouseprimarybutton-f-sys.md#setmouseprimarybutton-1) | Sets the primary mouse button. This API uses an asynchronous callback to return the result. |
| [setMousePrimaryButton](arkts-input-pointer-setmouseprimarybutton-f-sys.md#setmouseprimarybutton-2) | Sets the primary mouse button. This API uses a promise to return the result. |
| [setMouseScrollDirection](arkts-input-pointer-setmousescrolldirection-f-sys.md#setmousescrolldirection-1) | Sets the scroll direction of the mouse wheel. This API uses a promise to return the result asynchronously. |
| [setMouseScrollRows](arkts-input-pointer-setmousescrollrows-f-sys.md#setmousescrollrows-1) | Sets the number of mouse scroll lines. This API uses an asynchronous callback to return the result. |
| [setMouseScrollRows](arkts-input-pointer-setmousescrollrows-f-sys.md#setmousescrollrows-2) | Sets the number of mouse scroll lines. This API uses a promise to return the result. |
| [setPointerColor](arkts-input-pointer-setpointercolor-f-sys.md#setpointercolor-1) | Sets the mouse pointer color. This API uses an asynchronous callback to return the result. |
| [setPointerColor](arkts-input-pointer-setpointercolor-f-sys.md#setpointercolor-2) | Sets the mouse pointer color. This API uses a promise to return the result. |
| [setPointerColorSync](arkts-input-pointer-setpointercolorsync-f-sys.md#setpointercolorsync-1) | Sets the pointer color. This API returns the result synchronously. |
| [setPointerSize](arkts-input-pointer-setpointersize-f-sys.md#setpointersize-1) | Sets the mouse pointer size. This API uses an asynchronous callback to return the result. |
| [setPointerSize](arkts-input-pointer-setpointersize-f-sys.md#setpointersize-2) | Sets the mouse pointer size. This API uses a promise to return the result. |
| [setPointerSizeSync](arkts-input-pointer-setpointersizesync-f-sys.md#setpointersizesync-1) | Sets the pointer size. This API returns the result synchronously. |
| [setPointerSpeed](arkts-input-pointer-setpointerspeed-f-sys.md#setpointerspeed-1) | Sets the mouse pointer speed. This API uses an asynchronous callback to return the result. |
| [setPointerSpeed](arkts-input-pointer-setpointerspeed-f-sys.md#setpointerspeed-2) | Sets the mouse pointer speed. This API uses a promise to return the result. |
| [setPointerSpeedSync](arkts-input-pointer-setpointerspeedsync-f-sys.md#setpointerspeedsync-1) | Sets the mouse pointer speed. This API returns the result synchronously. |
| [setTouchpadDoubleTapAndDragState](arkts-input-pointer-settouchpaddoubletapanddragstate-f-sys.md#settouchpaddoubletapanddragstate-1) | Sets the touchpad double-tap and drag switch state. This API uses an asynchronous callback to return the result. |
| [setTouchpadDoubleTapAndDragState](arkts-input-pointer-settouchpaddoubletapanddragstate-f-sys.md#settouchpaddoubletapanddragstate-2) | Sets the touchpad double-tap and drag switch state. This API uses a promise to return the result. |
| [setTouchpadPinchSwitch](arkts-input-pointer-settouchpadpinchswitch-f-sys.md#settouchpadpinchswitch-1) | Sets the touchpad pinch switch. This API uses an asynchronous callback to return the result. |
| [setTouchpadPinchSwitch](arkts-input-pointer-settouchpadpinchswitch-f-sys.md#settouchpadpinchswitch-2) | Sets the touchpad pinch switch. This API uses a promise to return the result. |
| [setTouchpadPointerSpeed](arkts-input-pointer-settouchpadpointerspeed-f-sys.md#settouchpadpointerspeed-1) | Sets the touchpad pointer speed. This API uses an asynchronous callback to return the result. |
| [setTouchpadPointerSpeed](arkts-input-pointer-settouchpadpointerspeed-f-sys.md#settouchpadpointerspeed-2) | Sets the touchpad pointer speed. This API uses a promise to return the result. |
| [setTouchpadRightClickType](arkts-input-pointer-settouchpadrightclicktype-f-sys.md#settouchpadrightclicktype-1) | Sets the touchpad right-click menu type. This API uses an asynchronous callback to return the result. |
| [setTouchpadRightClickType](arkts-input-pointer-settouchpadrightclicktype-f-sys.md#settouchpadrightclicktype-2) | Sets the touchpad right-click menu type. This API uses a promise to return the result. |
| [setTouchpadScrollDirection](arkts-input-pointer-settouchpadscrolldirection-f-sys.md#settouchpadscrolldirection-1) | Sets the touchpad scroll direction. This API uses an asynchronous callback to return the result. |
| [setTouchpadScrollDirection](arkts-input-pointer-settouchpadscrolldirection-f-sys.md#settouchpadscrolldirection-2) | Sets the touchpad scroll direction. This API uses a promise to return the result. |
| [setTouchpadScrollSwitch](arkts-input-pointer-settouchpadscrollswitch-f-sys.md#settouchpadscrollswitch-1) | Sets the touchpad scroll switch. This API uses an asynchronous callback to return the result. |
| [setTouchpadScrollSwitch](arkts-input-pointer-settouchpadscrollswitch-f-sys.md#settouchpadscrollswitch-2) | Sets the touchpad scroll switch. This API uses a promise to return the result. |
| [setTouchpadSwipeSwitch](arkts-input-pointer-settouchpadswipeswitch-f-sys.md#settouchpadswipeswitch-1) | Sets the touchpad multi-finger swipe switch. This API uses an asynchronous callback to return the result. |
| [setTouchpadSwipeSwitch](arkts-input-pointer-settouchpadswipeswitch-f-sys.md#settouchpadswipeswitch-2) | Sets the touchpad multi-finger swipe switch. This API uses a promise to return the result. |
| [setTouchpadTapSwitch](arkts-input-pointer-settouchpadtapswitch-f-sys.md#settouchpadtapswitch-1) | Sets the touchpad tap switch. This API uses an asynchronous callback to return the result. |
| [setTouchpadTapSwitch](arkts-input-pointer-settouchpadtapswitch-f-sys.md#settouchpadtapswitch-2) | Sets the touchpad tap switch. This API uses a promise to return the result. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [CursorConfig](arkts-input-pointer-cursorconfig-i.md) | Defines custom cursor configuration. |
| [CustomCursor](arkts-input-pointer-customcursor-i.md) | Defines custom cursor resources. |

### Enums

| Name | Description |
| --- | --- |
| [PointerStyle](arkts-input-pointer-pointerstyle-e.md) | Mouse pointer style types. |
| [PrimaryButton](arkts-input-pointer-primarybutton-e.md) | Type of the primary mouse button. |
| [RightClickType](arkts-input-pointer-rightclicktype-e.md) | Enumerates shortcut menu triggering modes. |
