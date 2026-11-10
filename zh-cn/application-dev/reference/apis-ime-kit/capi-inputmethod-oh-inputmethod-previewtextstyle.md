# OH_InputMethod_PreviewTextStyle
<!--Kit: IME Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @codexu62-->
<!--Designer: @zhaolinglan-->
<!--Tester: @murphy84-->
<!--Adviser: @zhang_yixin13-->

## 概述

描述预上屏文本的样式。此类型为不透明类型，使用[inputmethod_preview_text_style_capi.h](capi-inputmethod-preview-text-style-capi-h.md)提供的接口访问属性，不能自行定义成员或按结构体字段布局访问。

由Create创建的对象初始样式为NONE，颜色为0，HasUnderlineColor输出false。调用SetUnderlineColor成功后，HasUnderlineColor输出true；没有单独设置该标志的接口。

应用创建的对象须配对销毁。样式回调传入的对象归框架管理，应用应在回调内读取需要的数据，不得销毁或保留指针供回调结束后访问。

**引用文件：** \<inputmethod/inputmethod_preview_text_style_capi.h>

**相关模块：** [InputMethod](capi-inputmethod.md)

**起始版本：** 26.1.0
