# InputMethod_TextAvoidInfo

```c
typedef struct InputMethod_TextAvoidInfo InputMethod_TextAvoidInfo
```

## 概述

输入框避让信息结构体，描述编辑框在物理屏幕上的位置和高度信息。输入法框架根据TextAvoidInfo中的positionY和height计算避让区域，使编辑框在软键盘弹起时能够自动上移或调整布局，确保输入区域不被键盘遮挡，保证用户可见并可操作输入内容。

**起始版本：** 12

**相关模块：** [InputMethod](capi-inputmethod.md)

**所在头文件：** [inputmethod_text_avoid_info_capi.h](capi-inputmethod-text-avoid-info-capi-h.md)

