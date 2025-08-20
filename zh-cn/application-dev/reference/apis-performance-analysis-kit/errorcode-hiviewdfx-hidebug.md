# HiDebug错误码

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @hello_harmony; @yu_haoqiaida-->
<!--Designer: @kutcherzhou1-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @foryourself-->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 11400101 系统服务获取失败

**错误信息**

ServiceId invalid. The system ability does not exist.

**错误描述**
当前serviceId未查询到对应的系统服务。

**可能原因**

serviceId参数无效，或对应的服务未启动。

**处理步骤**

确保传入正确的系统服务serviceId。

## 11400102 重复采集

**错误信息**

Capture trace already enabled.

**错误描述**
进程已开启trace采集。

**可能原因**

进程正在进行trace采集。

**处理步骤**

等待trace采集结束或调用OH_HiDebug_StopAppTraceCapture关闭正在运行的trace采集。

## 11400103 权限校验失败

**错误信息**

No write permission on the file.

**错误描述**
当前目录没有权限写trace文件。

**可能原因**

目录不存在或被误删。

**处理步骤**

重新运行采集接口，再次生成正确的目录文件。

## 11400104 内部异常

**错误信息**

Abnormal trace status.

**错误描述**
当前trace采集内部状态异常。

**可能原因**

系统内核崩溃或应用进程卡死。

**处理步骤**

建议重启应用或系统。

## 11400105 未开启trace采集

**错误信息**

No capture trace running.

**错误描述**
当前没有trace正在采集。

**可能原因**

未开启trace采集。

**处理步骤**

开启trace采集，然后停止。

## 11400106 接口调用配额已超出

**错误信息**

Quota exceeded.

**错误描述**
接口调用配额已超出。

**可能原因**

1.进程调用次数超出配额（1次/天）。

2.整机调用次数超出配额（5次/周）。

**处理步骤**

等待进程或整机的调用配额刷新。

## 11400107 dump子进程fork失败

**错误信息**

Fork operation failed.

**错误描述**
dump子进程fork失败。

**可能原因**

系统资源不足，建议检查系统负载。

**处理步骤**

建议开发者重试。若重试后依然失败，请通过[日志分析](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-setup-hilog)过滤error级别日志辅助问题定位。若依然无法解决，<!--RP1-->可向官方反馈。<!--RP1End-->

## 11400108 等待dump子进程结束失败

**错误信息**

Failed to wait for the child process to finish.

**错误描述**
等待dump子进程结束失败。

**可能原因**

系统资源不足，建议检查系统负载。

**处理步骤**

建议开发者重试。若重试后依然失败，请通过[日志分析](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-setup-hilog)过滤error级别日志辅助问题定位。若依然无法解决，<!--RP1-->可向官方反馈。<!--RP1End-->

## 11400109 等待dump子进程超时

**错误信息**

Timeout while waiting for the child process to finish.

**错误描述**
等待dump子进程结束超时。

**可能原因**

dump过程耗时长，建议检查系统负载。

**处理步骤**

建议开发者重试。若重试后依然失败，请通过[日志分析](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-setup-hilog)过滤error级别日志辅助问题定位。若依然无法解决，<!--RP1-->可向官方反馈。<!--RP1End-->

## 11400110 磁盘空间不足

**错误信息**

Failed to create dump file.

**错误描述**
磁盘空间不足。

**可能原因**

磁盘可用空间少于30GB。

**处理步骤**

释放磁盘空间，确保空闲空间大于30GB。

## 11400111 Napi接口调用失败

**错误信息**

Napi interface call exception.

**错误描述**
Napi接口调用时出现异常。

**可能原因**

虚拟机发生异常。

**处理步骤**

建议开发者重试。若重试后依然失败，请通过[日志分析](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-setup-hilog)过滤error级别日志辅助问题定位。若依然无法解决，<!--RP1-->可向官方反馈。<!--RP1End-->

## 11400112 重复dump采集

**错误信息**

Repeated data dump.

**错误描述**
重复进行dump数据采集。

**可能原因**

该接口已被调用，在调用未结束时发生了重复调用。

**处理步骤**

建议优化代码逻辑，确保上次dump完成后，再启动新的dump。

## 11400113 创建dump文件失败

**错误信息**

Failed to create dump file.

**错误描述**

创建dump文件时出现失败。

**可能原因**

1、进程目录下存在同名文件。

2、系统资源不足。

**处理步骤**

建议开发者重试。若重试后依然失败，请通过[日志分析](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-setup-hilog)过滤error级别日志辅助问题定位。若依然无法解决，<!--RP1-->可向官方反馈。<!--RP1End-->

## 11400114 使能GWP-Asan失败

**错误信息**

The number of GWP-ASAN applications of this device overflowed after last boot.

**错误描述**

设备在本次启动后，使能GWP-Asan的应用数量超出系统限制。

**可能原因**

单设备运行期间最多支持20个应用使能GWP-Asan，已超出配额限制。

**处理步骤**

重启系统刷新整机配额。