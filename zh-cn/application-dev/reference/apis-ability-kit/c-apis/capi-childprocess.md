# ChildProcess

## 概述

提供用于管理子进程的接口。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**起始版本：** 12
## 文件汇总

| 名称 | 描述 |
| -- | -- |
| [native_child_process.h](capi-native-child-process-h.md) | 支持创建Native子进程，并在父子进程间建立IPC通道，适用于需要将耗时任务、高风险操作或独立业务逻辑隔离到独立进程执行的多种场景。该模块提供了进程隔离、IPC通信、灵活配置等核心能力，可以有效提升应用的稳定性和安全性，避免主进程阻塞或崩溃。通过子进程机制，开发者可以实现多进程架构，将计算密集型任务、媒体处理、网络请求等业务独立运行，提升应用的响应速度和用户体验。 |
