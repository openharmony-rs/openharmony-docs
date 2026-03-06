# Display (V1_4)

## 概述

显示模块驱动接口定义。

提供给上层图形服务使用的驱动接口，包括图层管理、设备控制、显示内存管理等相关接口。

**起始版本：**  6.1

## 汇总

### 文件

| 名称 | 描述 |
| -------- | -------- |
| [IAllocator.idl](_buffer_i_allocator_8idl_v14.md) | 显示内存分配接口声明。 |

### 结构体

| 名称 | 描述 |
| -------- | -------- |
| interface&nbsp;&nbsp;[IAllocator](_buffer_interface_i_allocator_v14.md) | 定义显示内存分配接口，基于v1_0.IAllocator增加bufferhandle克隆接口CloneDmaBufferHandle。 |
