# 全局快捷键管理错误码

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @Brilliantry_Rui-->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 4200002 快捷键被系统注册

**错误信息**

The hotkey has been used by the system.

**错误描述**

快捷键已经被系统应用注册，会产生此错误码。

**可能原因**

1. 快捷键已经被系统应用注册。

**处理步骤**

1. 可以通过[getAllSystemHotkeys](js-apis-inputconsumer.md#inputconsumergetallsystemhotkeys)接口查询所有的系统快捷键。

## 4200003 快捷键已经被三方注册

**错误信息**

The hotkey has been subscribed to by another.

**错误描述**

快捷键被其他三方应用注册，会产生此错误码。

**可能原因**

1. 快捷键已经被其他三方应用注册。

**处理步骤**

1. 在cmd命令窗口执行(hidumper -s 3101 -a -s)查询已经被注册的快捷键，注册未被三方占用的快捷键。