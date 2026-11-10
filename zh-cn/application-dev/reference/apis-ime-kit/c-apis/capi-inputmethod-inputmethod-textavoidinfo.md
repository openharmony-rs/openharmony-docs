# InputMethod_TextAvoidInfo

```c
typedef struct InputMethod_TextAvoidInfo InputMethod_TextAvoidInfo
```

## 概述

输入框避让信息结构体，描述编辑框在物理屏幕上的位置和高度信息。输入法框架根据TextAvoidInfo中的positionY和height计算避让 区域，使编辑框在软键盘弹起时能够自动上移或调整布局，确保输入区域不被键盘遮挡，保证用户可见并可操作输入内容。 <br> <br>用途：作为编辑框避让键盘区域的参数载体，向输入法框架传递编辑框的垂直位置和高度信息。输入法框架根据positionY（编辑框顶 部Y坐标，取值原则：大于等于0的有效屏幕Y坐标）和height（编辑框高度， 取值原则：大于0的有效高度值）确定编辑框在屏幕上的完整垂直范围（positionY到positionY+height），并与键盘占据的屏幕区域进行比较， 计算是否需要避让以及避让的偏移量。 <br> <br>使用场景：在编辑框与输入法服务绑定后（通过OH_InputMethodController_Attach），编辑框客户端通过 InputMethod_TextConfig将TextAvoidInfo传递给输入法框架。输入法框架在键盘弹起时读取避让信息，判断编辑框是否处于键盘遮挡区域，并 触发相应的避让调整。该结构体也可由输入法应用读取，用于了解编辑框的屏幕位置以优化键盘布局。 <br> <br>相关函数：<br>
\| 函数 \| 说明 \|
\| --- \| --- \|
\| [OH_TextAvoidInfo_Create](capi-inputmethod-text-avoid-info-capi-h.md#oh_textavoidinfo_create) \| 创建 InputMethod_TextAvoidInfo实例 \|
\| [OH_TextAvoidInfo_Destroy](capi-inputmethod-text-avoid-info-capi-h.md#oh_textavoidinfo_destroy) \| 销毁 InputMethod_TextAvoidInfo实例 \|
\| [OH_TextAvoidInfo_SetPositionY](capi-inputmethod-text-avoid-info-capi-h. md#oh_textavoidinfo_setpositiony) \| 设置Y坐标值 \|
\| [OH_TextAvoidInfo_SetHeight](capi-inputmethod-text-avoid-info-capi-h.md#oh_textavoidinfo_setheight) \| 设置高度值 \|
\| [OH_TextAvoidInfo_GetPositionY](capi-inputmethod-text-avoid-info-capi-h. md#oh_textavoidinfo_getpositiony) \| 获取Y坐标值 \|
\| [OH_TextAvoidInfo_GetHeight](capi-inputmethod-text-avoid-info-capi-h.md#oh_textavoidinfo_getheight) \| 获取高度值 \|
\| [OH_TextConfig_GetTextAvoidInfo](capi-inputmethod-text-config-capi-h. md#oh_textconfig_gettextavoidinfo) \| 从TextConfig中获取TextAvoidInfo \| <br> <br>相关结构体：<br>
\| 结构体 \| 说明 \|
\| --- \| --- \|
\| [InputMethod_TextConfig](capi-inputmethod-inputmethod-textconfig.md) \| 文本输入框配置结构体，TextAvoidInfo作 为其子属性被包含 \| <br> <br>句柄与所有权：仅可使用本API创建的有效句柄或框架提供的借用句柄；仅可销毁独立创建的对象。 回调提供的对象和TextConfig的子对象视图均为借用对象。访问接口对未注册或已失效的句柄返回IME_ERR_PARAMCHECK， NULL参数仍按原有规则返回错误。 <br>保护边界：生命周期检查不保证对象成员的线程安全，也不能在地址复用后识别所有失效地址。 对象销毁后应将指针置空；不得在回调结束后保留回调对象。

<!--Device-typedef struct InputMethod_TextAvoidInfo InputMethod_TextAvoidInfo--><!--Device-typedef struct InputMethod_TextAvoidInfo InputMethod_TextAvoidInfo-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**起始版本：** 12

**相关模块：** [InputMethod](capi-ime-kit-inputmethod.md)

**所在头文件：** [inputmethod_text_avoid_info_capi.h](capi-inputmethod-text-avoid-info-capi-h.md)

