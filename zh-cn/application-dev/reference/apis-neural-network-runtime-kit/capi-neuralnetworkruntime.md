# NeuralNetworkRuntime
<!--Kit: Neural Network Runtime Kit-->
<!--Subsystem: AI-->
<!--Owner: @GbuzhidaoR-->
<!--SE: @GbuzhidaoR-->
<!--TSE @GbuzhidaoR-->

## 概述

提供Neural Network Runtime加速模型推理的相关接口。

**起始版本：** 9
## 文件汇总

| 名称 | 描述 |
| -- | -- |
| [neural_network_core.h](capi-neural-network-core-h.md) | Neural Network Core模块接口定义，AI推理框架使用Neural Network Core提供的Native接口，完成模型编译，并在加速硬件上执行推理和计算。<br> 部分接口定义从neural_network_runtime.h移动至此头文件统一呈现，对于此类接口，API version 11 版本之前即支持使用，各版本均可正常使用。<br/>Neural Network Core的接口目前均不支持多线程并发调用。 |
| [neural_network_runtime.h](capi-neural-network-runtime-h.md) | Neural Network Runtime模块接口定义，AI推理框架使用Neural Network Runtime提供的Native接口，完成模型构建。<br/>Neural Network Runtime的接口目前均不支持多线程并发调用。 |
| [neural_network_runtime_type.h](capi-neural-network-runtime-type-h.md) | Neural Network Runtime定义的结构体和枚举值。 |
