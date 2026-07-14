# @ohos.multimodalInput.pointer

本模块提供鼠标光标管理能力，包括查询、设置鼠标光标属性。

> **说明**：

**起始版本：** 9

**系统能力：** SystemCapability.MultimodalInput.Input.Pointer

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getPointerStyle](arkts-input-getpointerstyle-f.md#getpointerstyle-1) | 获取指定窗口的鼠标样式类型，此接口仅支持获取本应用进程内窗口的鼠标样式类型，使用callback异步回调。 |
| [getPointerStyle](arkts-input-getpointerstyle-f.md#getpointerstyle-2) | 获取鼠标样式类型，此接口仅支持获取本应用进程内窗口的鼠标样式类型，使用Promise异步回调。 |
| [getPointerStyleSync](arkts-input-getpointerstylesync-f.md#getpointerstylesync-1) | 查询指定窗口的鼠标样式类型，如向东箭头、向西箭头、向南箭头、向北箭头等。此接口仅支持获取本应用进程内窗口的鼠标样式类型。 |
| [isPointerVisible](arkts-input-ispointervisible-f.md#ispointervisible-1) | 获取鼠标光标显示状态，使用callback异步回调。 |
| [isPointerVisible](arkts-input-ispointervisible-f.md#ispointervisible-2) | 获取鼠标光标显示状态，使用Promise异步回调。 |
| [isPointerVisibleSync](arkts-input-ispointervisiblesync-f.md#ispointervisiblesync-1) | 获取当前窗口鼠标光标的显示状态，使用同步方式。 |
| [setCustomCursor](arkts-input-setcustomcursor-f.md#setcustomcursor-1) | 设置指定窗口的自定义光标样式，此接口仅支持设置本应用进程内窗口的自定义光标样式，如需通过UIExtensionAbility进程设置宿主窗口的自定义光标样式，请参阅[setCustomCursor](../../../../reference/apis-arkui/arkts-apis-uicontext-cursorcontroller.md#setcustomcursor)，使用Promise异步回调。 |
| [setCustomCursor](arkts-input-setcustomcursor-f.md#setcustomcursor-2) | 设置指定窗口的自定义光标样式，此接口仅支持设置本应用进程内窗口的自定义光标样式，如需通过UIExtensionAbility进程设置宿主窗口的自定义光标样式，请参阅[setCustomCursor](../../../../reference/apis-arkui/arkts-apis-uicontext-cursorcontroller.md#setcustomcursor)，使用Promise异步回调。应用窗口布局改变、热区切换、页面跳转、光标移出再回到窗口、光标在窗口不同区域移动，以上场景可能导致光标切换回系统样式，需要开发者重新设置光标样式。 |
| [setCustomCursorSync](arkts-input-setcustomcursorsync-f.md#setcustomcursorsync-1) | 设置指定窗口的自定义光标样式，使用同步方式进行设置。此接口仅支持设置本应用进程内窗口的自定义光标样式，如需通过UIExtensionAbility进程设置宿主窗口的自定义光标样式，请参阅[setCustomCursor](../../../../reference/apis-arkui/arkts-apis-uicontext-cursorcontroller.md#setcustomcursor)。 |
| [setPointerStyle](arkts-input-setpointerstyle-f.md#setpointerstyle-1) | 设置指定窗口的鼠标样式类型，此接口仅支持设置本应用进程内窗口的鼠标样式类型，如需通过UIExtensionAbility进程设置宿主窗口的鼠标样式类型，请参阅[setCursor](../../../../reference/apis-arkui/arkts-apis-uicontext-cursorcontroller.md#setcursor12)，使用callback异步回调。 |
| [setPointerStyle](arkts-input-setpointerstyle-f.md#setpointerstyle-2) | 设置指定窗口的鼠标样式类型，此接口仅支持设置本应用进程内窗口的鼠标样式类型，如需通过UIExtensionAbility进程设置宿主窗口的鼠标样式类型，请参阅[setCursor](../../../../reference/apis-arkui/arkts-apis-uicontext-cursorcontroller.md#setcursor12)，使用Promise异步回调。 |
| [setPointerStyleSync](arkts-input-setpointerstylesync-f.md#setpointerstylesync-1) | 设置指定窗口的鼠标样式类型，使用同步方式返回结果。此接口仅支持设置本应用进程内窗口的鼠标样式类型，如需通过UIExtensionAbility进程设置宿主窗口的鼠标样式类型，请参阅[setCursor](../../../../reference/apis-arkui/arkts-apis-uicontext-cursorcontroller.md#setcursor12)。 |
| [setPointerVisible](arkts-input-setpointervisible-f.md#setpointervisible-1) | 设置当前窗口的鼠标光标是否显示，使用callback异步回调。 |
| [setPointerVisible](arkts-input-setpointervisible-f.md#setpointervisible-2) | 设置当前窗口的鼠标光标是否显示，使用Promise异步回调。 |
| [setPointerVisibleSync](arkts-input-setpointervisiblesync-f.md#setpointervisiblesync-1) | 设置当前窗口鼠标光标的显示状态，使用同步方式。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getHoverScrollState](arkts-input-gethoverscrollstate-f-sys.md#gethoverscrollstate-1) | 获取鼠标悬停滚动开关状态，使用callback异步回调。 |
| [getHoverScrollState](arkts-input-gethoverscrollstate-f-sys.md#gethoverscrollstate-2) | 获取当前鼠标悬停滚动开关状态，使用Promise异步回调。 |
| [getMousePrimaryButton](arkts-input-getmouseprimarybutton-f-sys.md#getmouseprimarybutton-1) | 获取当前鼠标主键，使用callback异步回调。 |
| [getMousePrimaryButton](arkts-input-getmouseprimarybutton-f-sys.md#getmouseprimarybutton-2) | 获取当前鼠标主键，使用Promise异步回调。 |
| [getMouseScrollDirection](arkts-input-getmousescrolldirection-f-sys.md#getmousescrolldirection-1) | 获取鼠标滚轮滚动方向，使用Promise异步回调。 |
| [getMouseScrollRows](arkts-input-getmousescrollrows-f-sys.md#getmousescrollrows-1) | 获取鼠标滚动行数，使用callback异步回调。 |
| [getMouseScrollRows](arkts-input-getmousescrollrows-f-sys.md#getmousescrollrows-2) | 获取当前鼠标滚动行数，使用Promise异步回调。 |
| [getPointerColor](arkts-input-getpointercolor-f-sys.md#getpointercolor-1) | 获取鼠标光标颜色，使用callback异步回调。 |
| [getPointerColor](arkts-input-getpointercolor-f-sys.md#getpointercolor-2) | 获取当前鼠标光标颜色，使用Promise异步回调。 |
| [getPointerColorSync](arkts-input-getpointercolorsync-f-sys.md#getpointercolorsync-1) | 获取鼠标光标颜色，使用同步方式返回结果。 |
| [getPointerSize](arkts-input-getpointersize-f-sys.md#getpointersize-1) | 获取鼠标光标大小，使用callback异步回调。 |
| [getPointerSize](arkts-input-getpointersize-f-sys.md#getpointersize-2) | 获取当前鼠标光标大小，使用Promise异步回调。 |
| [getPointerSizeSync](arkts-input-getpointersizesync-f-sys.md#getpointersizesync-1) | 获取鼠标光标大小，使用同步方式返回结果。 |
| [getPointerSpeed](arkts-input-getpointerspeed-f-sys.md#getpointerspeed-1) | 获取鼠标移动速度，使用callback异步回调。 |
| [getPointerSpeed](arkts-input-getpointerspeed-f-sys.md#getpointerspeed-2) | 获取当前鼠标移动速度，使用Promise异步回调。 |
| [getPointerSpeedSync](arkts-input-getpointerspeedsync-f-sys.md#getpointerspeedsync-1) | 使用同步方式获取当前鼠标移动速度。 |
| [getTouchpadDoubleTapAndDragState](arkts-input-gettouchpaddoubletapanddragstate-f-sys.md#gettouchpaddoubletapanddragstate-1) | 获取触控板双击拖拽开关的开启状态，使用callback异步回调。 |
| [getTouchpadDoubleTapAndDragState](arkts-input-gettouchpaddoubletapanddragstate-f-sys.md#gettouchpaddoubletapanddragstate-2) | 获取触控板双击拖拽开关的开启状态，使用Promise异步回调。 |
| [getTouchpadPinchSwitch](arkts-input-gettouchpadpinchswitch-f-sys.md#gettouchpadpinchswitch-1) | 获取触控板双指捏合功能开启状态，使用callback异步回调。 |
| [getTouchpadPinchSwitch](arkts-input-gettouchpadpinchswitch-f-sys.md#gettouchpadpinchswitch-2) | 获取触控板双指捏合功能开启状态，使用Promise异步回调。 |
| [getTouchpadPointerSpeed](arkts-input-gettouchpadpointerspeed-f-sys.md#gettouchpadpointerspeed-1) | 获取触控板光标移动速度，使用callback异步回调。 |
| [getTouchpadPointerSpeed](arkts-input-gettouchpadpointerspeed-f-sys.md#gettouchpadpointerspeed-2) | 获取触控板光标移动速度，使用Promise异步回调。 |
| [getTouchpadRightClickType](arkts-input-gettouchpadrightclicktype-f-sys.md#gettouchpadrightclicktype-1) | 获取触控板右键菜单类型，使用callback异步回调。 |
| [getTouchpadRightClickType](arkts-input-gettouchpadrightclicktype-f-sys.md#gettouchpadrightclicktype-2) | 获取触控板右键菜单类型，使用Promise异步回调。 |
| [getTouchpadScrollDirection](arkts-input-gettouchpadscrolldirection-f-sys.md#gettouchpadscrolldirection-1) | 获取触控板滚轴方向，使用callback异步回调。 |
| [getTouchpadScrollDirection](arkts-input-gettouchpadscrolldirection-f-sys.md#gettouchpadscrolldirection-2) | 获取触控板滚轴方向，使用Promise异步回调。 |
| [getTouchpadScrollSwitch](arkts-input-gettouchpadscrollswitch-f-sys.md#gettouchpadscrollswitch-1) | 获取触控板滚轴能力开启状态，使用callback异步回调。 |
| [getTouchpadScrollSwitch](arkts-input-gettouchpadscrollswitch-f-sys.md#gettouchpadscrollswitch-2) | 获取触控板滚轴能力开启状态，使用Promise异步回调。 |
| [getTouchpadSwipeSwitch](arkts-input-gettouchpadswipeswitch-f-sys.md#gettouchpadswipeswitch-1) | 获取触控板多指滑动功能开启状态，使用callback异步回调。 |
| [getTouchpadSwipeSwitch](arkts-input-gettouchpadswipeswitch-f-sys.md#gettouchpadswipeswitch-2) | 获取触控板多指滑动功能开启状态，使用Promise异步回调。 |
| [getTouchpadTapSwitch](arkts-input-gettouchpadtapswitch-f-sys.md#gettouchpadtapswitch-1) | 获取触控板轻触能力开启状态，使用callback异步回调。 |
| [getTouchpadTapSwitch](arkts-input-gettouchpadtapswitch-f-sys.md#gettouchpadtapswitch-2) | 获取触控板轻触功能开启状态，使用Promise异步回调。 |
| [setHoverScrollState](arkts-input-sethoverscrollstate-f-sys.md#sethoverscrollstate-1) | 设置鼠标悬停滚动开关状态，使用callback异步回调。 |
| [setHoverScrollState](arkts-input-sethoverscrollstate-f-sys.md#sethoverscrollstate-2) | 设置鼠标悬停滚动开关状态，使用Promise异步回调。 |
| [setMousePrimaryButton](arkts-input-setmouseprimarybutton-f-sys.md#setmouseprimarybutton-1) | 设置鼠标主键，使用callback异步回调。 |
| [setMousePrimaryButton](arkts-input-setmouseprimarybutton-f-sys.md#setmouseprimarybutton-2) | 设置鼠标主键，使用Promise异步回调。 |
| [setMouseScrollDirection](arkts-input-setmousescrolldirection-f-sys.md#setmousescrolldirection-1) | 设置鼠标滚轮滚动的方向，使用Promise异步回调。 |
| [setMouseScrollRows](arkts-input-setmousescrollrows-f-sys.md#setmousescrollrows-1) | 设置鼠标滚动行数，使用callback异步回调。 |
| [setMouseScrollRows](arkts-input-setmousescrollrows-f-sys.md#setmousescrollrows-2) | 设置鼠标滚动行数，使用Promise异步回调。 |
| [setPointerColor](arkts-input-setpointercolor-f-sys.md#setpointercolor-1) | 设置鼠标光标颜色，使用callback异步回调。&gt; **说明**：&gt;&gt; 设置和调试时，需连接外部设备，如鼠标、蓝牙等。 |
| [setPointerColor](arkts-input-setpointercolor-f-sys.md#setpointercolor-2) | 设置鼠标光标颜色，使用Promise异步回调。&gt; **说明**：&gt;&gt; 设置和调试时，需连接外部设备，如鼠标、蓝牙等。 |
| [setPointerColorSync](arkts-input-setpointercolorsync-f-sys.md#setpointercolorsync-1) | 设置鼠标光标颜色，使用同步方式进行设置。&gt; **说明**：&gt;&gt; 设置和调试时，需连接外部设备，如鼠标、蓝牙等。 |
| [setPointerSize](arkts-input-setpointersize-f-sys.md#setpointersize-1) | 设置鼠标光标大小，使用callback异步回调。 |
| [setPointerSize](arkts-input-setpointersize-f-sys.md#setpointersize-2) | 设置鼠标光标大小，使用Promise异步回调。 |
| [setPointerSizeSync](arkts-input-setpointersizesync-f-sys.md#setpointersizesync-1) | 设置鼠标光标大小，使用同步方式进行设置。 |
| [setPointerSpeed](arkts-input-setpointerspeed-f-sys.md#setpointerspeed-1) | 设置鼠标移动速度，使用callback异步回调。 |
| [setPointerSpeed](arkts-input-setpointerspeed-f-sys.md#setpointerspeed-2) | 设置鼠标移动速度，使用Promise异步回调。 |
| [setPointerSpeedSync](arkts-input-setpointerspeedsync-f-sys.md#setpointerspeedsync-1) | 使用同步方式设置鼠标移动速度。 |
| [setTouchpadDoubleTapAndDragState](arkts-input-settouchpaddoubletapanddragstate-f-sys.md#settouchpaddoubletapanddragstate-1) | 设置触控板双击拖拽开关状态，使用callback异步回调。 |
| [setTouchpadDoubleTapAndDragState](arkts-input-settouchpaddoubletapanddragstate-f-sys.md#settouchpaddoubletapanddragstate-2) | 设置触控板双击拖拽开关状态，使用Promise异步回调。 |
| [setTouchpadPinchSwitch](arkts-input-settouchpadpinchswitch-f-sys.md#settouchpadpinchswitch-1) | 设置触控板双指捏合功能开关，使用callback异步回调。 |
| [setTouchpadPinchSwitch](arkts-input-settouchpadpinchswitch-f-sys.md#settouchpadpinchswitch-2) | 设置触控板双指捏合功能开关，使用Promise异步回调。 |
| [setTouchpadPointerSpeed](arkts-input-settouchpadpointerspeed-f-sys.md#settouchpadpointerspeed-1) | 设置触控板光标移动速度，使用callback异步回调。 |
| [setTouchpadPointerSpeed](arkts-input-settouchpadpointerspeed-f-sys.md#settouchpadpointerspeed-2) | 设置触控板光标移动速度，使用Promise异步回调。 |
| [setTouchpadRightClickType](arkts-input-settouchpadrightclicktype-f-sys.md#settouchpadrightclicktype-1) | 设置触控板右键菜单类型，使用callback异步回调。 |
| [setTouchpadRightClickType](arkts-input-settouchpadrightclicktype-f-sys.md#settouchpadrightclicktype-2) | 设置触控板右键菜单类型，使用Promise异步回调。 |
| [setTouchpadScrollDirection](arkts-input-settouchpadscrolldirection-f-sys.md#settouchpadscrolldirection-1) | 设置触控板滚轴的方向，使用callback异步回调。 |
| [setTouchpadScrollDirection](arkts-input-settouchpadscrolldirection-f-sys.md#settouchpadscrolldirection-2) | 设置触控板滚轴的方向，使用Promise异步回调。 |
| [setTouchpadScrollSwitch](arkts-input-settouchpadscrollswitch-f-sys.md#settouchpadscrollswitch-1) | 设置触控板滚轴开关，使用callback异步回调。 |
| [setTouchpadScrollSwitch](arkts-input-settouchpadscrollswitch-f-sys.md#settouchpadscrollswitch-2) | 设置触控板滚轴开关，使用Promise异步回调。 |
| [setTouchpadSwipeSwitch](arkts-input-settouchpadswipeswitch-f-sys.md#settouchpadswipeswitch-1) | 设置触控板多指滑动功能开关，使用callback异步回调。 |
| [setTouchpadSwipeSwitch](arkts-input-settouchpadswipeswitch-f-sys.md#settouchpadswipeswitch-2) | 设置触控板多指滑动功能开关，使用Promise异步回调。 |
| [setTouchpadTapSwitch](arkts-input-settouchpadtapswitch-f-sys.md#settouchpadtapswitch-1) | 设置触控板轻触功能开关，使用callback异步回调。 |
| [setTouchpadTapSwitch](arkts-input-settouchpadtapswitch-f-sys.md#settouchpadtapswitch-2) | 设置触控板轻触功能开关，使用Promise异步回调。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [CursorConfig](arkts-input-cursorconfig-i.md) | 自定义光标配置。 |
| [CustomCursor](arkts-input-customcursor-i.md) | 自定义光标资源。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [PointerStyle](arkts-input-pointerstyle-e.md) | 鼠标光标样式类型。 |
| [PrimaryButton](arkts-input-primarybutton-e.md) | 鼠标主键类型。 |
| [RightClickType](arkts-input-rightclicktype-e.md) | 右键菜单的触发方式。 |

