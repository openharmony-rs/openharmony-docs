# uitest错误码

<!--Kit: Test Kit-->
<!--Subsystem: Test-->
<!--Owner: @inter515-->
<!--Designer: @inter515-->
<!--Tester: @laonie666-->
<!--Adviser: @Brilliantry_Rui-->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 17000001 初始化失败

**错误信息**

Initialization failed.

**错误描述**

框架初始化失败。

**可能原因**

无法连接到无障碍服务。

**处理步骤**

执行param set persist.ace.testmode.enabled 1，并重启设备。

## 17000002 当前无法调用
**错误信息**

The async function is not called with await.

**错误描述**

API没有被异步调用。

**可能原因**

API没有使用await进行异步调用，造成堵塞。

**处理步骤**

检查测试用例，确保异步接口使用await调用。

## 17000003 断言失败
**错误信息**

Assertion failed.

**错误描述**

用户断言失败。

**可能原因**

用户断言存在的控件实际不存在。

**处理步骤**

检查用户断言存在的控件实际是否存在。

## 17000004 目标控件/窗口丢失
**错误信息**

The window or component is invisible or destroyed.

**错误描述**

目标控件/窗口丢失，无法进行操作。

**可能原因**

获取到目标控件/窗口后，页面发生变化导致目标丢失。

**处理步骤**

检查获取到目标控件/窗口后，页面是否发生变化导致目标丢失。

## 17000005 操作不支持
**错误信息**

This operation is not supported.

**错误描述**

UI对象不支持该操作。

**可能原因**

当前界面控件/窗口属性/设备不支持该操作。

**处理步骤**

检查当前界面控件/窗口属性/设备是否支持该操作。

## 17000007 参数不合法
**错误信息**

Parameter verification failed.

**错误描述**

参数校验失败。

**可能原因**

参数类型错误/参数取值超出规定范围。

**处理步骤**

检查接口入参是否符合要求。
