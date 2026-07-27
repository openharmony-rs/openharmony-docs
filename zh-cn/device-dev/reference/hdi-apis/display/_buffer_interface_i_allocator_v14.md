# IAllocator

## 概述

定义显示内存分配接口，基于v1_0.IAllocator增加bufferhandle克隆接口CloneDmaBufferHandle。

**起始版本：**  6.1

**相关模块：**  [Display](_buffer_display_v14.md)

## 汇总

### Public 成员函数

| 名称 | 描述 |
| -------- | -------- |
| [CloneDmaBufferHandle](#clonedmabufferhandle) ([in] NativeBuffer inHandle, [out] NativeBuffer outHandle) | bufferhandle克隆接口。 |

## 成员函数说明

### CloneDmaBufferHandle()

```idl
IAllocator::CloneDmaBufferHandle([in] NativeBuffer inHandle, [out] NativeBuffer outHandle)
```

**描述**

bufferhandle克隆接口。

**起始版本：**  6.1

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| inHandle | 传入的内存handle。 |
| outHandle | 克隆后的内存handle。 |

**返回：**

返回0，表示执行成功。

返回其他值表示执行失败，具体错误码查看[DispErrCode](_display_v10.md#disperrcode)。
