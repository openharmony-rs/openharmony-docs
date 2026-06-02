# 应用灰度错误码

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @lyj_love_code-->
<!--Designer: @tangyyan-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 36000001 

**错误信息**

Initialization error. Possibly caused by invoking this function before invoking init function.

**错误描述**

应用灰度初始化异常。

**可能原因**

没有完成应用灰度的初始化。

**处理步骤**

在调用该接口之前，先调用[hiRetrieval.init()](js-apis-hiretrieval.md#hiretrievalinit)接口完成应用灰度的初始化。

## 36000002 

**错误信息**

Multi-instance applications not supported error. Possibly caused by invoking this function in a multi-instance application.

**错误描述**

多实例应用调用[hiRetrieval.init()](js-apis-hiretrieval.md#hiretrievalinit)接口异常。

**可能原因**

当前版本暂不支持多实例应用调用应用灰度的能力。

**处理步骤**

当前版本暂不支持多实例应用调用应用灰度的能力。