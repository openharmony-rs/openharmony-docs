# 键鼠穿越管理错误码（待停用）

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->

> **说明：**
>
> - 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码](../errorcode-universal.md)。

## 20900001 服务异常

**错误信息**

Service exception. Possible causes:
1. A system error, such as null pointer, container-related exception, or IPC exception.
2. N-API invocation exception or invalid N-API status.

**错误描述**

当调用键鼠穿越接口时系统内部发生异常，会产生此错误码。

**可能原因**

1. 系统内部错误，如空指针、容器相关异常或IPC异常。
2. N-API调用异常或无效的N-API状态。

**处理步骤**

1. 检查系统服务是否正常运行，尝试重新执行操作。
2. 如果问题持续存在，请联系技术支持。

## 4400001 目标设备描述符错误

**错误信息**

Incorrect descriptor for the target device.

**错误描述**

当调用键鼠穿越接口传入无效的设备描述符参数时，系统会产生此错误码。

**可能原因**

1. 穿越目标设备不存在（设备未组网）。
2. 目标设备描述符为空。

**处理步骤**

1. 请确认键鼠穿越目标设备是否已正确与本地设备完整组网。
2. 请正确使用穿越目标设备的设备描述符。

## 4400002 操作输入设备失败

**错误信息**

Screen hop failed.

**错误描述**

当调用键鼠穿越接口时穿越状态异常，系统会产生此错误码。

**可能原因**

1. 发起键鼠穿越时，本机键鼠穿越为穿出状态。
2. 关闭键鼠穿越时，本机键鼠穿越为自由态。
3. 发起关闭键鼠穿越时，本机键鼠穿越状态正在切换中。

**处理步骤**

1. 发起键鼠穿越时，请检查本机键鼠穿越状态是否为非穿出状态。
2. 关闭键鼠穿越时，请检查本机键鼠穿越状态是否为非自由态。
3. 发起关闭键鼠穿越时，请检查本机键鼠穿越状态是否在切换中。