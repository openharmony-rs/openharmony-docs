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

当开发者调用[startImageAnalyzer()](ts-basic-components-xcomponent.md#startimageanalyzer12)接口时，若当前不支持AI图像分析功能，会抛出此错误码。

**可能原因**

调用了当前设备不支持的AI图像分析接口（[startImageAnalyzer()](ts-basic-components-xcomponent.md#startimageanalyzer12)）。

**处理步骤**

1. AI图像分析功能依赖设备能力，目前无主动查询接口，可在调用[startImageAnalyzer()](ts-basic-components-xcomponent.md#startimageanalyzer12)时通过捕获错误码110001判断设备是否支持。
2. 若设备不支持，则不调用[startImageAnalyzer()](ts-basic-components-xcomponent.md#startimageanalyzer12)接口，或引导用户更换支持的设备。

## 110002 AI图像分析正在进行中

**错误信息**

Image analysis is currently being executed.

**错误描述**

当开发者调用[startImageAnalyzer()](ts-basic-components-xcomponent.md#startimageanalyzer12)接口时，若上一次的分析还没有结束，会抛出此错误码。

**可能原因**

在AI图像分析未结束时（上一次分析未返回结果）再次调用了[startImageAnalyzer()](ts-basic-components-xcomponent.md#startimageanalyzer12)接口。

**处理步骤**

1. 请等待上一次[startImageAnalyzer()](ts-basic-components-xcomponent.md#startimageanalyzer12)接口的分析完成（通过Promise或回调返回结果）后，再发起新一次的[startImageAnalyzer()](ts-basic-components-xcomponent.md#startimageanalyzer12)调用。
2. 避免在分析进行中重复调用同一接口。

## 110003 AI图像分析已停止

**错误信息**

Image analysis is stopped.

**错误描述**

当开发者调用[stopImageAnalyzer()](ts-basic-components-xcomponent.md#stopimageanalyzer12)接口时，若当前AI图像分析尚未完成，会抛出此错误码。

**可能原因**

在AI图像分析未完成时调用了[stopImageAnalyzer()](ts-basic-components-xcomponent.md#stopimageanalyzer12)接口。

**处理步骤**

1. 请确认在调用[stopImageAnalyzer()](ts-basic-components-xcomponent.md#stopimageanalyzer12)接口前，[startImageAnalyzer()](ts-basic-components-xcomponent.md#startimageanalyzer12)接口已返回结果（即上一次分析已结束）。
2. 检查接口调用顺序，避免在分析未完成时调用停止接口。
