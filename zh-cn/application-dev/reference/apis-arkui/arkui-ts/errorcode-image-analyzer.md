# 图像AI分析错误码
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liyujie43-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @Brilliantry_Rui-->

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../../errorcode-universal.md)。

## 110001 AI图像分析功能不支持

**错误信息**

Image analysis feature is unsupported.

**错误描述**

当开发者调用startImageAnalyzer()接口时，若当前不支持AI图像分析功能，会抛出此错误码。

**可能原因**

调用不支持的功能接口。

**处理步骤**

NA

## 110002 AI图像分析正在进行中

**错误信息**

Image analysis is currently being executed.

**错误描述**

当开发者调用startImageAnalyzer()接口时，若上一次的分析还没有结束，会抛出此错误码。

**可能原因**

调用接口时机错误。

**处理步骤**

NA

## 110003 AI图像分析已停止

**错误信息**

Image analysis is stopped.

**错误描述**

当开发者调用[stopImageAnalyzer()](ts-basic-components-xcomponent.md#stopimageanalyzer12)接口时，若当前存在正在进行的AI图像分析（startImageAnalyzer的Promise尚未返回），会停止当前分析并向该Promise抛出110003，表示分析已被停止。

**可能原因**

在AI图像分析进行中（startImageAnalyzer的Promise尚未返回）时调用了[stopImageAnalyzer()](ts-basic-components-xcomponent.md#stopimageanalyzer12)接口，导致当前分析被停止并向startImageAnalyzer的Promise抛出110003。

**处理步骤**

1. 请确认在调用[stopImageAnalyzer()](ts-basic-components-xcomponent.md#stopimageanalyzer12)接口前，[startImageAnalyzer()](ts-basic-components-xcomponent.md#startimageanalyzer12)接口已返回结果（即上一次分析已通过Promise回调返回结果，无论成功或失败）。
2. 检查接口调用顺序，避免在分析未完成时调用停止接口。
