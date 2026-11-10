# HiDebug SharedHeapObjectUsedSize错误码

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @leiguangyu-->
<!--Designer: @mgce1-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 11400104 虚拟机实例异常

**错误信息**

VM instance exception.

**错误描述**

虚拟机实例异常。

**可能原因**

系统资源耗尽。

**处理步骤**

重启系统后重启应用。

### 触发场景1：线程创建失败、fd 耗尽、内存映射失败。

**错误信息**

VM instance exception.

**错误描述**

虚拟机实例异常。

**可能原因**

1. 线程数达到系统上限，创建线程失败。
2. fd达到上限无法申请。
3. 系统内存不足，内存映射失败。

**处理步骤**

1. 关闭暂时不用进程，等待系统回收资源后重新分配。
2. 重启系统后重启应用，一次性释放所有资源占用。
