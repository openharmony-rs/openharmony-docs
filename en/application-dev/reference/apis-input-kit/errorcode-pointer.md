# Mouse Pointer Error Codes

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @Brilliantry_Rui-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 26500001 Invalid Window ID

**Error Message**

Invalid windowId. Possible causes: The window id does not belong to the current process.

**Description**

Invalid window ID.

**Possible Causes**

The window ID does not belong to the current process.

**Solution**

Pass in the window ID of the current process. You can obtain the attributes of the current window by calling [getWindowProperties()](../apis-arkui/arkts-apis-window-Window.md#getwindowproperties9). The window ID is contained in the returned window attributes.

## 3800001 Multimodal input internal error

**Error Message**

Input service exception. Possible causes: 1. Memory allocation failure. 2. Thread busy. 3. Service terminated abnormally. 4. Other unexpected errors. Try again later.

**Description**

Internal error of the multimodal input service.

**Possible Causes**

Unexpected errors, such as memory allocation failure, busy thread, and abnormal service exit, occur.

**Solution**

Try again later.
