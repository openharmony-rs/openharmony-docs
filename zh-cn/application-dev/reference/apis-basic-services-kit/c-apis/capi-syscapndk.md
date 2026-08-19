# SyscapNdk

## 概述

Provides APIs for querying system capabilities.

**起始版本：** 8
## 文件汇总

| 名称 | 描述 |
| -- | -- |
| [syscap_ndk.h](capi-syscap-ndk-h.md) | 查询单个系统能力（SystemCapability）是否被支持的API。开发者可在运行时查询设备是否支持特定系统能力，实现差异化功能适配。典型使用场景包括：针对不同设备型号适配功能、特性降级开关控制、条件功能分支判断等。该API具有轻量级、高效的特点，能帮助开发者避免因调用设备不支持的API而导致的崩溃问题，提高应用在不同设备上的兼容性和稳定性。 |
