# @ohos.multimodalInput.pointer

本模块提供鼠标光标管理能力，包括查询、设置鼠标光标属性。 > **说明：**

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare namespace pointer--><!--Device-unnamed-declare namespace pointer-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Pointer

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getPointerStyle](arkts-input-pointer-getpointerstyle-f.md#getPointerStyle) | 获取指定窗口的鼠标样式类型，此接口仅支持获取本应用进程内窗口的鼠标样式类型，使用callback异步回调。 |
| [getPointerStyle](arkts-input-pointer-getpointerstyle-f.md#getPointerStyle) | 获取鼠标样式类型，此接口仅支持获取本应用进程内窗口的鼠标样式类型，使用Promise异步回调。 |
| [getPointerStyleSync](arkts-input-pointer-getpointerstylesync-f.md#getPointerStyleSync) | 查询指定窗口的鼠标样式类型，如向东箭头、向西箭头、向南箭头、向北箭头等。此接口仅支持获取本应用进程内窗口的鼠标样式类型。 |
| [isPointerVisible](arkts-input-pointer-ispointervisible-f.md#isPointerVisible) | 获取鼠标光标显示状态，使用callback异步回调。 |
| [isPointerVisible](arkts-input-pointer-ispointervisible-f.md#isPointerVisible) | 获取鼠标光标显示状态，使用Promise异步回调。 |
| [isPointerVisibleSync](arkts-input-pointer-ispointervisiblesync-f.md#isPointerVisibleSync) | 获取当前窗口鼠标光标的显示状态，使用同步方式。 |
| [setCustomCursor](arkts-input-pointer-setcustomcursor-f.md#setCustomCursor) | 设置指定窗口的自定义光标样式，此接口仅支持设置本应用进程内窗口的自定义光标样式，如需通过UIExtensionAbility进程设置宿主窗口的自定义光标样式，请参阅 [setCustomCursor](../../../reference/apis-arkui/arkts-apis-uicontext-cursorcontroller.md#setcustomcursor)，使用 Promise异步回调。 |
| [setCustomCursor](arkts-input-pointer-setcustomcursor-f.md#setCustomCursor) | 设置指定窗口的自定义光标样式，此接口仅支持设置本应用进程内窗口的自定义光标样式，如需通过UIExtensionAbility进程设置宿主窗口的自定义光标样式，请参阅 [setCustomCursor](../../../reference/apis-arkui/arkts-apis-uicontext-cursorcontroller.md#setcustomcursor)，使用 Promise异步回调。 应用窗口布局改变、热区切换、页面跳转、光标移出再回到窗口、光标在窗口不同区域移动，以上场景可能导致光标切换回系统样式，需要开发者重新设置光标样式。 |
| [setCustomCursorSync](arkts-input-pointer-setcustomcursorsync-f.md#setCustomCursorSync) | 设置指定窗口的自定义光标样式，使用同步方式进行设置。此接口仅支持设置本应用进程内窗口的自定义光标样式，如需通过UIExtensionAbility进程设置宿主窗口的自定义光标样式，请参阅 [setCustomCursor](../../../reference/apis-arkui/arkts-apis-uicontext-cursorcontroller.md#setcustomcursor)。 |
| [setPointerStyle](arkts-input-pointer-setpointerstyle-f.md#setPointerStyle) | 设置指定窗口的鼠标样式类型，此接口仅支持设置本应用进程内窗口的鼠标样式类型，如需通过UIExtensionAbility进程设置宿主窗口的鼠标样式类型，请参阅 [setCursor](../../../reference/apis-arkui/arkts-apis-uicontext-cursorcontroller.md#setcursor12)，使用callback异步回调。 |
| [setPointerStyle](arkts-input-pointer-setpointerstyle-f.md#setPointerStyle) | 设置指定窗口的鼠标样式类型，此接口仅支持设置本应用进程内窗口的鼠标样式类型，如需通过UIExtensionAbility进程设置宿主窗口的鼠标样式类型，请参阅 [setCursor](../../../reference/apis-arkui/arkts-apis-uicontext-cursorcontroller.md#setcursor12)，使用Promise异步回调。 |
| [setPointerStyleSync](arkts-input-pointer-setpointerstylesync-f.md#setPointerStyleSync) | 设置指定窗口的鼠标样式类型，使用同步方式返回结果。此接口仅支持设置本应用进程内窗口的鼠标样式类型，如需通过UIExtensionAbility进程设置宿主窗口的鼠标样式类型，请参阅 [setCursor](../../../reference/apis-arkui/arkts-apis-uicontext-cursorcontroller.md#setcursor12)。 |
| [setPointerVisible](arkts-input-pointer-setpointervisible-f.md#setPointerVisible) | 设置当前窗口的鼠标光标是否显示，使用callback异步回调。 |
| [setPointerVisible](arkts-input-pointer-setpointervisible-f.md#setPointerVisible) | 设置当前窗口的鼠标光标是否显示，使用Promise异步回调。 |
| [setPointerVisibleSync](arkts-input-pointer-setpointervisiblesync-f.md#setPointerVisibleSync) | 设置当前窗口鼠标光标的显示状态，使用同步方式。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getHoverScrollState](arkts-input-pointer-gethoverscrollstate-f-sys.md#getHoverScrollState) | 获取鼠标悬停滚动开关状态，使用callback异步回调。 |
| [getHoverScrollState](arkts-input-pointer-gethoverscrollstate-f-sys.md#getHoverScrollState（系统接口）) | 获取当前鼠标悬停滚动开关状态，使用Promise异步回调。 |
| [getMousePrimaryButton](arkts-input-pointer-getmouseprimarybutton-f-sys.md#getMousePrimaryButton) | 获取当前鼠标主键，使用callback异步回调。 |
| [getMousePrimaryButton](arkts-input-pointer-getmouseprimarybutton-f-sys.md#getMousePrimaryButton（系统接口）) | 获取当前鼠标主键，使用Promise异步回调。 |
| [getMouseScrollDirection](arkts-input-pointer-getmousescrolldirection-f-sys.md#getMouseScrollDirection) | 获取鼠标滚轮滚动方向，使用Promise异步回调。 |
| [getMouseScrollRows](arkts-input-pointer-getmousescrollrows-f-sys.md#getMouseScrollRows) | 获取鼠标滚动行数，使用callback异步回调。 |
| [getMouseScrollRows](arkts-input-pointer-getmousescrollrows-f-sys.md#getMouseScrollRows（系统接口）) | 获取当前鼠标滚动行数，使用Promise异步回调。 |
| [getPointerColor](arkts-input-pointer-getpointercolor-f-sys.md#getPointerColor) | 获取鼠标光标颜色，使用callback异步回调。 |
| [getPointerColor](arkts-input-pointer-getpointercolor-f-sys.md#getPointerColor（系统接口）) | 获取当前鼠标光标颜色，使用Promise异步回调。 |
| [getPointerColorSync](arkts-input-pointer-getpointercolorsync-f-sys.md#getPointerColorSync) | 获取鼠标光标颜色，使用同步方式返回结果。 |
| [getPointerSize](arkts-input-pointer-getpointersize-f-sys.md#getPointerSize) | 获取鼠标光标大小，使用callback异步回调。 |
| [getPointerSize](arkts-input-pointer-getpointersize-f-sys.md#getPointerSize（系统接口）) | 获取当前鼠标光标大小，使用Promise异步回调。 |
| [getPointerSizeSync](arkts-input-pointer-getpointersizesync-f-sys.md#getPointerSizeSync) | 获取鼠标光标大小，使用同步方式返回结果。 |
| [getPointerSpeed](arkts-input-pointer-getpointerspeed-f-sys.md#getPointerSpeed) | 获取鼠标移动速度，使用callback异步回调。 |
| [getPointerSpeed](arkts-input-pointer-getpointerspeed-f-sys.md#getPointerSpeed（系统接口）) | 获取当前鼠标移动速度，使用Promise异步回调。 |
| [getPointerSpeedSync](arkts-input-pointer-getpointerspeedsync-f-sys.md#getPointerSpeedSync) | 使用同步方式获取当前鼠标移动速度。 |
| [getTouchpadDoubleTapAndDragState](arkts-input-pointer-gettouchpaddoubletapanddragstate-f-sys.md#getTouchpadDoubleTapAndDragState) | 获取触控板双击拖拽开关的开启状态，使用callback异步回调。 |
| [getTouchpadDoubleTapAndDragState](arkts-input-pointer-gettouchpaddoubletapanddragstate-f-sys.md#getTouchpadDoubleTapAndDragState（系统接口）) | 获取触控板双击拖拽开关的开启状态，使用Promise异步回调。 |
| [getTouchpadPinchSwitch](arkts-input-pointer-gettouchpadpinchswitch-f-sys.md#getTouchpadPinchSwitch) | 获取触控板双指捏合功能开启状态，使用callback异步回调。 |
| [getTouchpadPinchSwitch](arkts-input-pointer-gettouchpadpinchswitch-f-sys.md#getTouchpadPinchSwitch（系统接口）) | 获取触控板双指捏合功能开启状态，使用Promise异步回调。 |
| [getTouchpadPointerSpeed](arkts-input-pointer-gettouchpadpointerspeed-f-sys.md#getTouchpadPointerSpeed) | 获取触控板光标移动速度，使用callback异步回调。 |
| [getTouchpadPointerSpeed](arkts-input-pointer-gettouchpadpointerspeed-f-sys.md#getTouchpadPointerSpeed（系统接口）) | 获取触控板光标移动速度，使用Promise异步回调。 |
| [getTouchpadRightClickType](arkts-input-pointer-gettouchpadrightclicktype-f-sys.md#getTouchpadRightClickType) | 获取触控板右键菜单类型，使用callback异步回调。 |
| [getTouchpadRightClickType](arkts-input-pointer-gettouchpadrightclicktype-f-sys.md#getTouchpadRightClickType（系统接口）) | 获取触控板右键菜单类型，使用Promise异步回调。 |
| [getTouchpadScrollDirection](arkts-input-pointer-gettouchpadscrolldirection-f-sys.md#getTouchpadScrollDirection) | 获取触控板滚轴方向，使用callback异步回调。 |
| [getTouchpadScrollDirection](arkts-input-pointer-gettouchpadscrolldirection-f-sys.md#getTouchpadScrollDirection（系统接口）) | 获取触控板滚轴方向，使用Promise异步回调。 |
| [getTouchpadScrollSwitch](arkts-input-pointer-gettouchpadscrollswitch-f-sys.md#getTouchpadScrollSwitch) | 获取触控板滚轴能力开启状态，使用callback异步回调。 |
| [getTouchpadScrollSwitch](arkts-input-pointer-gettouchpadscrollswitch-f-sys.md#getTouchpadScrollSwitch（系统接口）) | 获取触控板滚轴能力开启状态，使用Promise异步回调。 |
| [getTouchpadSwipeSwitch](arkts-input-pointer-gettouchpadswipeswitch-f-sys.md#getTouchpadSwipeSwitch) | 获取触控板多指滑动功能开启状态，使用callback异步回调。 |
| [getTouchpadSwipeSwitch](arkts-input-pointer-gettouchpadswipeswitch-f-sys.md#getTouchpadSwipeSwitch（系统接口）) | 获取触控板多指滑动功能开启状态，使用Promise异步回调。 |
| [getTouchpadTapSwitch](arkts-input-pointer-gettouchpadtapswitch-f-sys.md#getTouchpadTapSwitch) | 获取触控板轻触能力开启状态，使用callback异步回调。 |
| [getTouchpadTapSwitch](arkts-input-pointer-gettouchpadtapswitch-f-sys.md#getTouchpadTapSwitch（系统接口）) | 获取触控板轻触功能开启状态，使用Promise异步回调。 |
| [setHoverScrollState](arkts-input-pointer-sethoverscrollstate-f-sys.md#setHoverScrollState) | 设置鼠标悬停滚动开关状态，使用callback异步回调。 |
| [setHoverScrollState](arkts-input-pointer-sethoverscrollstate-f-sys.md#setHoverScrollState（系统接口）) | 设置鼠标悬停滚动开关状态，使用Promise异步回调。 |
| [setMousePrimaryButton](arkts-input-pointer-setmouseprimarybutton-f-sys.md#setMousePrimaryButton) | 设置鼠标主键，使用callback异步回调。 |
| [setMousePrimaryButton](arkts-input-pointer-setmouseprimarybutton-f-sys.md#setMousePrimaryButton（系统接口）) | 设置鼠标主键，使用Promise异步回调。 |
| [setMouseScrollDirection](arkts-input-pointer-setmousescrolldirection-f-sys.md#setMouseScrollDirection) | 设置鼠标滚轮滚动的方向，使用Promise异步回调。 |
| [setMouseScrollRows](arkts-input-pointer-setmousescrollrows-f-sys.md#setMouseScrollRows) | 设置鼠标滚动行数，使用callback异步回调。 |
| [setMouseScrollRows](arkts-input-pointer-setmousescrollrows-f-sys.md#setMouseScrollRows（系统接口）) | 设置鼠标滚动行数，使用Promise异步回调。 |
| [setPointerColor](arkts-input-pointer-setpointercolor-f-sys.md#setPointerColor) | 设置鼠标光标颜色，使用callback异步回调。 |
| [setPointerColor](arkts-input-pointer-setpointercolor-f-sys.md#setPointerColor（系统接口）) | 设置鼠标光标颜色，使用Promise异步回调。 |
| [setPointerColorSync](arkts-input-pointer-setpointercolorsync-f-sys.md#setPointerColorSync) | 设置鼠标光标颜色，使用同步方式进行设置。 |
| [setPointerSize](arkts-input-pointer-setpointersize-f-sys.md#setPointerSize) | 设置鼠标光标大小，使用callback异步回调。 |
| [setPointerSize](arkts-input-pointer-setpointersize-f-sys.md#setPointerSize（系统接口）) | 设置鼠标光标大小，使用Promise异步回调。 |
| [setPointerSizeSync](arkts-input-pointer-setpointersizesync-f-sys.md#setPointerSizeSync) | 设置鼠标光标大小，使用同步方式进行设置。 |
| [setPointerSpeed](arkts-input-pointer-setpointerspeed-f-sys.md#setPointerSpeed) | 设置鼠标移动速度，使用callback异步回调。 |
| [setPointerSpeed](arkts-input-pointer-setpointerspeed-f-sys.md#setPointerSpeed（系统接口）) | 设置鼠标移动速度，使用Promise异步回调。 |
| [setPointerSpeedSync](arkts-input-pointer-setpointerspeedsync-f-sys.md#setPointerSpeedSync) | 使用同步方式设置鼠标移动速度。 |
| [setTouchpadDoubleTapAndDragState](arkts-input-pointer-settouchpaddoubletapanddragstate-f-sys.md#setTouchpadDoubleTapAndDragState) | 设置触控板双击拖拽开关状态，使用callback异步回调。 |
| [setTouchpadDoubleTapAndDragState](arkts-input-pointer-settouchpaddoubletapanddragstate-f-sys.md#setTouchpadDoubleTapAndDragState（系统接口）) | 设置触控板双击拖拽开关状态，使用Promise异步回调。 |
| [setTouchpadPinchSwitch](arkts-input-pointer-settouchpadpinchswitch-f-sys.md#setTouchpadPinchSwitch) | 设置触控板双指捏合功能开关，使用callback异步回调。 |
| [setTouchpadPinchSwitch](arkts-input-pointer-settouchpadpinchswitch-f-sys.md#setTouchpadPinchSwitch（系统接口）) | 设置触控板双指捏合功能开关，使用Promise异步回调。 |
| [setTouchpadPointerSpeed](arkts-input-pointer-settouchpadpointerspeed-f-sys.md#setTouchpadPointerSpeed) | 设置触控板光标移动速度，使用callback异步回调。 |
| [setTouchpadPointerSpeed](arkts-input-pointer-settouchpadpointerspeed-f-sys.md#setTouchpadPointerSpeed（系统接口）) | 设置触控板光标移动速度，使用Promise异步回调。 |
| [setTouchpadRightClickType](arkts-input-pointer-settouchpadrightclicktype-f-sys.md#setTouchpadRightClickType) | 设置触控板右键菜单类型，使用callback异步回调。 |
| [setTouchpadRightClickType](arkts-input-pointer-settouchpadrightclicktype-f-sys.md#setTouchpadRightClickType（系统接口）) | 设置触控板右键菜单类型，使用Promise异步回调。 |
| [setTouchpadScrollDirection](arkts-input-pointer-settouchpadscrolldirection-f-sys.md#setTouchpadScrollDirection) | 设置触控板滚轴的方向，使用callback异步回调。 |
| [setTouchpadScrollDirection](arkts-input-pointer-settouchpadscrolldirection-f-sys.md#setTouchpadScrollDirection（系统接口）) | 设置触控板滚轴的方向，使用Promise异步回调。 |
| [setTouchpadScrollSwitch](arkts-input-pointer-settouchpadscrollswitch-f-sys.md#setTouchpadScrollSwitch) | 设置触控板滚轴开关，使用callback异步回调。 |
| [setTouchpadScrollSwitch](arkts-input-pointer-settouchpadscrollswitch-f-sys.md#setTouchpadScrollSwitch（系统接口）) | 设置触控板滚轴开关，使用Promise异步回调。 |
| [setTouchpadSwipeSwitch](arkts-input-pointer-settouchpadswipeswitch-f-sys.md#setTouchpadSwipeSwitch) | 设置触控板多指滑动功能开关，使用callback异步回调。 |
| [setTouchpadSwipeSwitch](arkts-input-pointer-settouchpadswipeswitch-f-sys.md#setTouchpadSwipeSwitch（系统接口）) | 设置触控板多指滑动功能开关，使用Promise异步回调。 |
| [setTouchpadTapSwitch](arkts-input-pointer-settouchpadtapswitch-f-sys.md#setTouchpadTapSwitch) | 设置触控板轻触功能开关，使用callback异步回调。 |
| [setTouchpadTapSwitch](arkts-input-pointer-settouchpadtapswitch-f-sys.md#setTouchpadTapSwitch（系统接口）) | 设置触控板轻触功能开关，使用Promise异步回调。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [CursorConfig](arkts-input-pointer-cursorconfig-i.md) | 自定义光标配置。 |
| [CustomCursor](arkts-input-pointer-customcursor-i.md) | 自定义光标资源。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [PointerStyle](arkts-input-pointer-pointerstyle-e.md) | 鼠标光标样式类型。 |
| [PrimaryButton](arkts-input-pointer-primarybutton-e.md) | 鼠标主键类型。 |
| [RightClickType](arkts-input-pointer-rightclicktype-e.md) | 右键菜单的触发方式。 |

