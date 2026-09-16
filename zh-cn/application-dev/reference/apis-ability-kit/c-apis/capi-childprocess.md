# ChildProcess

## 概述

提供子进程的管理能力，支持创建Native子进程并在父子进程间建立IPC通道，用于实现多进程应用开发。创建的子进程不支持UI界面，也不支持Context相关的接口调用。通过本模块和childProcessManager启动的子进程总数最大为512个，其中childProcessManager在SELF_FORK模式下启动的子进程不计入总数。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**起始版本：** 12

## 文件汇总

| 名称 | 描述 |
| -- | -- |
| [native_child_process.h](capi-native-child-process-h.md) | 支持创建Native子进程，并在父子进程间建立IPC通道，适用于需要将耗时任务、高风险操作或独立业务逻辑隔离到独立进程执行的多种场景。该模块提供了进程隔离、IPC通信、灵活配置等核心能力，可以有效提升应用的稳定性和安全性，避免主进程阻塞或崩溃。通过子进程机制，开发者可以实现多进程架构，将计算密集型任务、媒体处理、网络请求等业务独立运行，提升应用的响应速度和用户体验。<br>引用文件：<AbilityKit/native_child_process.h><br>库：libchild_process.so## 约束与限制### 功能限制- 创建的子进程不支持创建UI界面。- 创建的子进程不支持依赖Context的API调用（包括Context模块自身API及将Context实例作为入参的API）。- 仅允许在主进程中创建子进程，子进程内不支持再次创建子进程。### 规格限制- 通过本模块中定义的创建子进程的接口和childProcessManager中定义的创建子进程的接口启动的子进程总数最大为512个（系统资源充足情况下），其中startChildProcess接口在SELF_FORK模式下启动的子进程不计入总数内。 |
