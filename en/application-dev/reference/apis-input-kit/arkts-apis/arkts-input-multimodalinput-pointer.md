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
| [getPointerStyle](arkts-input-pointer-getpointerstyle-f.md#getpointerstyle1) | Obtains the mouse pointer style type of a specified window. This API can obtain only the mouse pointer style type of windows within the current application process. This API uses an asynchronous callback to return the result. |
| [getPointerStyle](arkts-input-pointer-getpointerstyle-f.md#getpointerstyle2) | Obtains the mouse pointer style type. This API can obtain only the mouse pointer style type of windows within the current application process. This API uses a promise to return the result. |
| [getPointerStyleSync](arkts-input-pointer-getpointerstylesync-f.md#getpointerstylesync) | Queries the mouse pointer style type of a specified window, such as east arrow, west arrow, south arrow, and north arrow. This API can obtain only the mouse pointer style type of windows within the current application process. |
| [getTouchpadScrollDirection](arkts-input-pointer-gettouchpadscrolldirection-f.md#gettouchpadscrolldirection1) | Obtains the touchpad scroll direction. This API uses an asynchronous callback to return the result. |
| [getTouchpadScrollDirection](arkts-input-pointer-gettouchpadscrolldirection-f.md#gettouchpadscrolldirection2) | Obtains the scroll direction of the touchpad. This API uses a promise to return the result. |
| [isPointerVisible](arkts-input-pointer-ispointervisible-f.md#ispointervisible1) | Obtains the display/hidden state of the current window. This state reflects the cursor display/hidden state of the multimodal process for the process where the window resides, not the actual cursor display/hidden status. Whether the cursor is correctly displayed/hidden is also affected by the render service process. This API uses an asynchronous callback to return the result. |
| [isPointerVisible](arkts-input-pointer-ispointervisible-f.md#ispointervisible2) | Obtains the display/hidden state of the current window. This state reflects the cursor display/hidden state of the multimodal process for the process where the window resides, not the actual cursor display/hidden status. Whether the cursor is correctly displayed/hidden is also affected by the render service process. This API uses a promise to return the result. |
| [isPointerVisibleSync](arkts-input-pointer-ispointervisiblesync-f.md#ispointervisiblesync) | Obtains the display/hidden state of the current window. This state reflects the cursor display/hidden state of the multimodal process for the process where the window resides, not the actual cursor display/hidden status. Whether the cursor is correctly displayed/hidden is also affected by the render service process. This API is called synchronously. |
| [setCustomCursor](arkts-input-pointer-setcustomcursor-f.md#setcustomcursor1) | Sets a custom pointer style for a specified window. This API can set only the custom pointer style of windows within the current application process. For details about how to set the custom pointer style of the host window through the **UIExtensionAbility** process, see [setCustomCursor](../../apis-arkui/arkts-apis/arkts-arkui-arkui-uicontext-cursorcontroller-c.md#setcustomcursor). This API uses a promise to return the result. |
| [setCustomCursor](arkts-input-pointer-setcustomcursor-f.md#setcustomcursor2) | Sets a custom pointer style for a specified window. This API can set only the custom pointer style of windows within the current application process. For details about how to set the custom pointer style of the host window through the **UIExtensionAbility** process, see [setCustomCursor](../../apis-arkui/arkts-apis/arkts-arkui-arkui-uicontext-cursorcontroller-c.md#setcustomcursor). This API uses a promise to return the result. |
| [setCustomCursorSync](arkts-input-pointer-setcustomcursorsync-f.md#setcustomcursorsync) | Sets a custom pointer style for a specified window synchronously. This API can set only the custom pointer style of windows within the current application process. For details about how to set the custom pointer style of the host window through the **UIExtensionAbility** process, see [setCustomCursor](../../apis-arkui/arkts-apis/arkts-arkui-arkui-uicontext-cursorcontroller-c.md#setcustomcursor). |
| [setPointerStyle](arkts-input-pointer-setpointerstyle-f.md#setpointerstyle1) | Sets the mouse pointer style type for a specified window. This API can set only the mouse pointer style type of windows within the current application process. For details about how to set the mouse pointer style type of the host window through the **UIExtensionAbility** process, see [setCursor](../../apis-arkui/arkts-apis/arkts-arkui-arkui-uicontext-cursorcontroller-c.md#setcursor). This API uses an asynchronous callback to return the result. |
| [setPointerStyle](arkts-input-pointer-setpointerstyle-f.md#setpointerstyle2) | Sets the mouse pointer style type for a specified window. This API can set only the mouse pointer style type of windows within the current application process. For details about how to set the mouse pointer style type of the host window through the **UIExtensionAbility** process, see [setCursor](../../apis-arkui/arkts-apis/arkts-arkui-arkui-uicontext-cursorcontroller-c.md#setcursor). This uses a promise to return the result. |
| [setPointerStyleSync](arkts-input-pointer-setpointerstylesync-f.md#setpointerstylesync) | Sets the mouse pointer style type for a specified window and returns the result synchronously. This API can set only the mouse pointer style type of windows within the current application process. For details about how to set the mouse pointer style type of the host window through the **UIExtensionAbility** process, see [setCursor](../../apis-arkui/arkts-apis/arkts-arkui-arkui-uicontext-cursorcontroller-c.md#setcursor). |
| [setPointerVisible](arkts-input-pointer-setpointervisible-f.md#setpointervisible1) | Sets the cursor display/hidden state. This state applies to all windows of the current process. The actual display/hidden effect of the cursor on the screen is also affected by the render service process. This API uses an asynchronous callback to return the result. |
| [setPointerVisible](arkts-input-pointer-setpointervisible-f.md#setpointervisible2) | Sets the cursor display/hidden state. This state applies to all windows of the current process. The actual display/hidden effect of the cursor on the screen is also affected by the render service process. This API uses a promise to return the result. |
| [setPointerVisibleSync](arkts-input-pointer-setpointervisiblesync-f.md#setpointervisiblesync) | Sets the cursor display/hidden state. This state applies to all windows of the current process. The actual display/hidden effect of the cursor on the screen is also affected by the render service process. This API is called synchronously. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getHoverScrollState](arkts-input-pointer-gethoverscrollstate-f-sys.md#gethoverscrollstate1) | Obtains the mouse hover scrolling switch state. This API uses an asynchronous callback to return the result. |
| [getHoverScrollState](arkts-input-pointer-gethoverscrollstate-f-sys.md#gethoverscrollstate2) | Obtains the status of the mouse hover scroll switch. This API uses a promise to return the result. |
| [getMousePrimaryButton](arkts-input-pointer-getmouseprimarybutton-f-sys.md#getmouseprimarybutton1) | Obtains the current primary mouse button. This API uses an asynchronous callback to return the result. |
| [getMousePrimaryButton](arkts-input-pointer-getmouseprimarybutton-f-sys.md#getmouseprimarybutton2) | Obtains the current primary mouse button. This API uses a promise to return the result. |
| [getMouseScrollDirection](arkts-input-pointer-getmousescrolldirection-f-sys.md#getmousescrolldirection) | Obtains the scroll direction of the mouse wheel. This API uses a promise to return the result asynchronously. |
| [getMouseScrollRows](arkts-input-pointer-getmousescrollrows-f-sys.md#getmousescrollrows1) | Obtains the number of mouse scroll lines. This API uses an asynchronous callback to return the result. |
| [getMouseScrollRows](arkts-input-pointer-getmousescrollrows-f-sys.md#getmousescrollrows2) | Obtains the number of mouse scroll lines. This API uses a promise to return the result. |
| [getPointerColor](arkts-input-pointer-getpointercolor-f-sys.md#getpointercolor1) | Obtains the mouse pointer color. This API uses an asynchronous callback to return the result. |
| [getPointerColor](arkts-input-pointer-getpointercolor-f-sys.md#getpointercolor2) | Obtains the current mouse pointer color. This API uses a promise to return the result. |
| [getPointerColorSync](arkts-input-pointer-getpointercolorsync-f-sys.md#getpointercolorsync) | Obtains the pointer color. This API returns the result synchronously. |
| [getPointerSize](arkts-input-pointer-getpointersize-f-sys.md#getpointersize1) | Obtains the current mouse pointer size. This API uses an asynchronous callback to return the result. |
| [getPointerSize](arkts-input-pointer-getpointersize-f-sys.md#getpointersize2) | Obtains the current mouse pointer size. This API uses a promise to return the result. |
| [getPointerSizeSync](arkts-input-pointer-getpointersizesync-f-sys.md#getpointersizesync) | Obtains the pointer size. This API returns the result synchronously. |
| [getPointerSpeed](arkts-input-pointer-getpointerspeed-f-sys.md#getpointerspeed1) | Obtains the mouse pointer speed. This API uses an asynchronous callback to return the result. |
| [getPointerSpeed](arkts-input-pointer-getpointerspeed-f-sys.md#getpointerspeed2) | Obtains the mouse pointer speed. This API uses a promise to return the result. |
| [getPointerSpeedSync](arkts-input-pointer-getpointerspeedsync-f-sys.md#getpointerspeedsync) | Obtains the mouse pointer speed. This API returns the result synchronously. |
| [getTouchpadDoubleTapAndDragState](arkts-input-pointer-gettouchpaddoubletapanddragstate-f-sys.md#gettouchpaddoubletapanddragstate1) | Obtains the touchpad double-tap and drag switch state. This API uses an asynchronous callback to return the result. |
| [getTouchpadDoubleTapAndDragState](arkts-input-pointer-gettouchpaddoubletapanddragstate-f-sys.md#gettouchpaddoubletapanddragstate2) | Obtains the touchpad double-tap and drag switch state. This API uses a promise to return the result. |
| [getTouchpadPinchSwitch](arkts-input-pointer-gettouchpadpinchswitch-f-sys.md#gettouchpadpinchswitch1) | Obtains the touchpad pinch switch state. This API uses an asynchronous callback to return the result. |
| [getTouchpadPinchSwitch](arkts-input-pointer-gettouchpadpinchswitch-f-sys.md#gettouchpadpinchswitch2) | Obtains the touchpad pinch switch state. This API uses a promise to return the result. |
| [getTouchpadPointerSpeed](arkts-input-pointer-gettouchpadpointerspeed-f-sys.md#gettouchpadpointerspeed1) | Obtains the touchpad pointer speed. This API uses an asynchronous callback to return the result. |
| [getTouchpadPointerSpeed](arkts-input-pointer-gettouchpadpointerspeed-f-sys.md#gettouchpadpointerspeed2) | Obtains the touchpad pointer speed. This API uses a promise to return the result. |
| [getTouchpadRightClickType](arkts-input-pointer-gettouchpadrightclicktype-f-sys.md#gettouchpadrightclicktype1) | Obtains the touchpad right-click menu type. This API uses an asynchronous callback to return the result. |
| [getTouchpadRightClickType](arkts-input-pointer-gettouchpadrightclicktype-f-sys.md#gettouchpadrightclicktype2) | Obtains the touchpad right-click menu type. This API uses a promise to return the result. |
| [getTouchpadScrollSwitch](arkts-input-pointer-gettouchpadscrollswitch-f-sys.md#gettouchpadscrollswitch1) | Obtains the touchpad scroll switch state. This API uses an asynchronous callback to return the result. |
| [getTouchpadScrollSwitch](arkts-input-pointer-gettouchpadscrollswitch-f-sys.md#gettouchpadscrollswitch2) | Obtains the touchpad scroll switch state. This API uses a promise to return the result. |
| [getTouchpadSwipeSwitch](arkts-input-pointer-gettouchpadswipeswitch-f-sys.md#gettouchpadswipeswitch1) | Obtains the touchpad multi-finger swipe switch state. This API uses an asynchronous callback to return the result. |
| [getTouchpadSwipeSwitch](arkts-input-pointer-gettouchpadswipeswitch-f-sys.md#gettouchpadswipeswitch2) | Obtains the touchpad multi-finger swipe switch state. This API uses a promise to return the result. |
| [getTouchpadTapSwitch](arkts-input-pointer-gettouchpadtapswitch-f-sys.md#gettouchpadtapswitch1) | Obtains the touchpad tap switch state. This API uses an asynchronous callback to return the result. |
| [getTouchpadTapSwitch](arkts-input-pointer-gettouchpadtapswitch-f-sys.md#gettouchpadtapswitch2) | Obtains the touchpad tap switch state. This API uses a promise to return the result. |
| [setHoverScrollState](arkts-input-pointer-sethoverscrollstate-f-sys.md#sethoverscrollstate1) | Sets the mouse hover scrolling switch state. This API uses an asynchronous callback to return the result. |
| [setHoverScrollState](arkts-input-pointer-sethoverscrollstate-f-sys.md#sethoverscrollstate2) | Sets the status of the mouse hover scroll switch. This API uses a promise to return the result. |
| [setMousePrimaryButton](arkts-input-pointer-setmouseprimarybutton-f-sys.md#setmouseprimarybutton1) | Sets the primary mouse button. This API uses an asynchronous callback to return the result. |
| [setMousePrimaryButton](arkts-input-pointer-setmouseprimarybutton-f-sys.md#setmouseprimarybutton2) | Sets the primary mouse button. This API uses a promise to return the result. |
| [setMouseScrollDirection](arkts-input-pointer-setmousescrolldirection-f-sys.md#setmousescrolldirection) | Sets the scroll direction of the mouse wheel. This API uses a promise to return the result asynchronously. |
| [setMouseScrollRows](arkts-input-pointer-setmousescrollrows-f-sys.md#setmousescrollrows1) | Sets the number of mouse scroll lines. This API uses an asynchronous callback to return the result. |
| [setMouseScrollRows](arkts-input-pointer-setmousescrollrows-f-sys.md#setmousescrollrows2) | Sets the number of mouse scroll lines. This API uses a promise to return the result. |
| [setPointerColor](arkts-input-pointer-setpointercolor-f-sys.md#setpointercolor1) | Sets the mouse pointer color. This API uses an asynchronous callback to return the result. |
| [setPointerColor](arkts-input-pointer-setpointercolor-f-sys.md#setpointercolor2) | Sets the mouse pointer color. This API uses a promise to return the result. |
| [setPointerColorSync](arkts-input-pointer-setpointercolorsync-f-sys.md#setpointercolorsync) | Sets the pointer color. This API returns the result synchronously. |
| [setPointerSize](arkts-input-pointer-setpointersize-f-sys.md#setpointersize1) | Sets the mouse pointer size. This API uses an asynchronous callback to return the result. |
| [setPointerSize](arkts-input-pointer-setpointersize-f-sys.md#setpointersize2) | Sets the mouse pointer size. This API uses a promise to return the result. |
| [setPointerSizeSync](arkts-input-pointer-setpointersizesync-f-sys.md#setpointersizesync) | Sets the pointer size. This API returns the result synchronously. |
| [setPointerSpeed](arkts-input-pointer-setpointerspeed-f-sys.md#setpointerspeed1) | Sets the mouse pointer speed. This API uses an asynchronous callback to return the result. |
| [setPointerSpeed](arkts-input-pointer-setpointerspeed-f-sys.md#setpointerspeed2) | Sets the mouse pointer speed. This API uses a promise to return the result. |
| [setPointerSpeedSync](arkts-input-pointer-setpointerspeedsync-f-sys.md#setpointerspeedsync) | Sets the mouse pointer speed. This API returns the result synchronously. |
| [setTouchpadDoubleTapAndDragState](arkts-input-pointer-settouchpaddoubletapanddragstate-f-sys.md#settouchpaddoubletapanddragstate1) | Sets the touchpad double-tap and drag switch state. This API uses an asynchronous callback to return the result. |
| [setTouchpadDoubleTapAndDragState](arkts-input-pointer-settouchpaddoubletapanddragstate-f-sys.md#settouchpaddoubletapanddragstate2) | Sets the touchpad double-tap and drag switch state. This API uses a promise to return the result. |
| [setTouchpadPinchSwitch](arkts-input-pointer-settouchpadpinchswitch-f-sys.md#settouchpadpinchswitch1) | Sets the touchpad pinch switch. This API uses an asynchronous callback to return the result. |
| [setTouchpadPinchSwitch](arkts-input-pointer-settouchpadpinchswitch-f-sys.md#settouchpadpinchswitch2) | Sets the touchpad pinch switch. This API uses a promise to return the result. |
| [setTouchpadPointerSpeed](arkts-input-pointer-settouchpadpointerspeed-f-sys.md#settouchpadpointerspeed1) | Sets the touchpad pointer speed. This API uses an asynchronous callback to return the result. |
| [setTouchpadPointerSpeed](arkts-input-pointer-settouchpadpointerspeed-f-sys.md#settouchpadpointerspeed2) | Sets the touchpad pointer speed. This API uses a promise to return the result. |
| [setTouchpadRightClickType](arkts-input-pointer-settouchpadrightclicktype-f-sys.md#settouchpadrightclicktype1) | Sets the touchpad right-click menu type. This API uses an asynchronous callback to return the result. |
| [setTouchpadRightClickType](arkts-input-pointer-settouchpadrightclicktype-f-sys.md#settouchpadrightclicktype2) | Sets the touchpad right-click menu type. This API uses a promise to return the result. |
| [setTouchpadScrollDirection](arkts-input-pointer-settouchpadscrolldirection-f-sys.md#settouchpadscrolldirection1) | Sets the touchpad scroll direction. This API uses an asynchronous callback to return the result. |
| [setTouchpadScrollDirection](arkts-input-pointer-settouchpadscrolldirection-f-sys.md#settouchpadscrolldirection2) | Sets the touchpad scroll direction. This API uses a promise to return the result. |
| [setTouchpadScrollSwitch](arkts-input-pointer-settouchpadscrollswitch-f-sys.md#settouchpadscrollswitch1) | Sets the touchpad scroll switch. This API uses an asynchronous callback to return the result. |
| [setTouchpadScrollSwitch](arkts-input-pointer-settouchpadscrollswitch-f-sys.md#settouchpadscrollswitch2) | Sets the touchpad scroll switch. This API uses a promise to return the result. |
| [setTouchpadSwipeSwitch](arkts-input-pointer-settouchpadswipeswitch-f-sys.md#settouchpadswipeswitch1) | Sets the touchpad multi-finger swipe switch. This API uses an asynchronous callback to return the result. |
| [setTouchpadSwipeSwitch](arkts-input-pointer-settouchpadswipeswitch-f-sys.md#settouchpadswipeswitch2) | Sets the touchpad multi-finger swipe switch. This API uses a promise to return the result. |
| [setTouchpadTapSwitch](arkts-input-pointer-settouchpadtapswitch-f-sys.md#settouchpadtapswitch1) | Sets the touchpad tap switch. This API uses an asynchronous callback to return the result. |
| [setTouchpadTapSwitch](arkts-input-pointer-settouchpadtapswitch-f-sys.md#settouchpadtapswitch2) | Sets the touchpad tap switch. This API uses a promise to return the result. |
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
