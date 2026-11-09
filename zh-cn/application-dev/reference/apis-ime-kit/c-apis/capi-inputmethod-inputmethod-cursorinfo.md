# InputMethod_CursorInfo

```c
typedef struct InputMethod_CursorInfo InputMethod_CursorInfo
```

## 概述

InputMethod_CursorInfo是光标信息的不透明类型（opaque type），用于描述文本输入时光标在物理屏幕上的位置和尺寸，包括光标 的水平坐标（left）、垂直坐标（top）、宽度（width）和高度（height）。 单位为px。 <br> <br>用途：为输入法服务提供光标的精确位置和尺寸信息，输入法根据此信息实现以下功能： <br>- 光标跟随：键盘面板根据光标位置调整显示位置，确保键盘不遮挡光标所在区域。 <br>- 候选词定位：输入法的候选词区域在光标附近显示，提供精准的输入体验。 <br>- 避让计算：输入法根据光标高度和位置计算需要避让的区域。 <br> <br>使用场景： <br>1. 在TextConfig中携带光标信息：应用在[OH_TextEditorProxy_GetTextConfigFunc](capi-inputmethod-text-editor-proxy-capi-h. md#oh_texteditorproxy_gettextconfigfunc)回调中返回TextConfig时，其中包含的 CursorInfo告知输入法当前光标位置和尺寸。 <br>2. 主动通知光标更新：当光标位置发生变化时（如用户移动光标、文本插入导致光标偏移），应用通过 [OH_InputMethodProxy_NotifyCursorUpdate](capi-inputmethod-inputmethod-proxy-capi-h. md#oh_inputmethodproxy_notifycursorupdate)主动通知输入法最新的光标位置。 <br> <br>与其他结构体的关系： <br>- 与InputMethod_TextConfig的关系：CursorInfo是TextConfig的子属性。应用在[OH_TextEditorProxy_GetTextConfigFunc] (capi-inputmethod-text-editor-proxy-capi-h. md#oh_texteditorproxy_gettextconfigfunc)回调中返回TextConfig时，TextConfig 内部包含CursorInfo，输入法通过[OH_TextConfig_GetCursorInfo](capi-inputmethod-text-config-capi-h. md#oh_textconfig_getcursorinfo)获取光标信息。因此应用需先创建CursorInfo并设置正确的光标坐标，然后在GetTextConfig回调中将 CursorInfo放入TextConfig。 <br>- 与OH_InputMethodProxy_NotifyCursorUpdate的关系：CursorInfo作为NotifyCursorUpdate函数的参数直接传入，用于在光标 位置变化时主动通知输入法。应用创建或更新CursorInfo后，通过NotifyCursorUpdate将最新光标信息发送给输入法。<br> <br>- 与InputMethod_InputMethodProxy的关系：NotifyCursorUpdate函数需要InputMethod_InputMethodProxy参数（由Attach返 回）和InputMethod_CursorInfo参数配合使用，inputMethodProxy标识交互通道，cursorInfo携带光标信息。 <br> <br>句柄与所有权：仅可使用本API创建的有效句柄或框架提供的借用句柄；仅可销毁独立创建的对象。 回调提供的对象和TextConfig的子对象视图均为借用对象。访问接口对未注册或已失效的句柄返回IME_ERR_PARAMCHECK， NULL参数仍按原有规则返回错误。 <br>保护边界：生命周期检查不保证对象成员的线程安全，也不能在地址复用后识别所有失效地址。 对象销毁后应将指针置空；不得在回调结束后保留回调对象。

<!--Device-typedef struct InputMethod_CursorInfo InputMethod_CursorInfo--><!--Device-typedef struct InputMethod_CursorInfo InputMethod_CursorInfo-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**起始版本：** 12

**相关模块：** [InputMethod](capi-ime-kit-inputmethod.md)

**所在头文件：** [inputmethod_cursor_info_capi.h](capi-inputmethod-cursor-info-capi-h.md)

