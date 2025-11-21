# 鼠标光标错误码

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @Brilliantry_Rui-->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 26500001 无效的windowId

**错误信息**

Invalid windowId. Possible causes: The window id does not belong to the current process.

**错误描述**

无效的窗口id。

**可能原因**

窗口id不属于当前进程。

**处理步骤**

请检查并传入当前进程的窗口ID，可通过windowClass.[getWindowProperties()](../apis-arkui/arkts-apis-window-Window.md#getwindowproperties9)接口获取当前窗口属性，窗口属性中含有窗口ID。

## 3800001 多模输入服务内部错误

**错误信息**

Input service exception. Possible causes: 1. Memory allocation failure. 2. Thread busy. 3. Service terminated abnormally. 4. Other unexpected errors. Try again later.

**错误描述**

多模输入服务内部错误。

**可能原因**

内存分配失败，线程繁忙，服务异常退出等非预期错误。

**处理步骤**

建议稍后重试。