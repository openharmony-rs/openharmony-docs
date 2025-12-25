# Global Shortcut Key Error Codes

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @Brilliantry_Rui-->

> **NOTE**
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](../errorcode-universal.md).

## 4200002 Shortcut Key Already Registered by a System Application

**Error Message**

The hotkey has been used by the system.

**Description**

This error code is reported if the shortcut key has been registered by a system application.

**Possible Cause**

1. The shortcut key has been registered by a system application.

**Solution**

1. You can call [getAllSystemHotkeys](js-apis-inputconsumer.md#inputconsumergetallsystemhotkeys) to query all system shortcut keys.

## 4200003 Shortcut Key Already Registered by a Third-party Application

**Error Message**

The hotkey has been subscribed to by another.

**Description**

This error code is generated when the shortcut key is registered by a third-party application.

**Possible Cause**

1. The shortcut key has been registered by a third-party application.

**Solution**

1. In the cmd window, run **hidumper -s 3101 -a -s** to query all registered shortcut keys and use any available shortcut keys.

## 3800001 Multimodal input internal error

**Error Message**

Input service exception. Possible causes: 1. Memory allocation failure. 2. Thread busy. 3. Service terminated abnormally. 4. Other unexpected errors. Try again later.

**Description**

Internal error of the multimodal input service.

**Possible Cause**

Unexpected errors, such as memory allocation failure, busy thread, and abnormal service exit, occur.

**Solution**

Try again later.
