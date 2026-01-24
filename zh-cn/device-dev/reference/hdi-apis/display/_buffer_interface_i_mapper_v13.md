# IMapper

## 概述

定义释放显示内存接口，基于v1_2.IMapper增加内存申请接口AllocMem，二次申请内存接口ReAllocMem，直通模式调用判断接口IsSupportAllocPassthrough。

**起始版本：**  6.0

**相关模块：**  [Display](_buffer_display_v13.md)

## 汇总

### Public 成员函数

| 名称 | 描述 |
| -------- | -------- |
| [AllocMem](#allocmem) ([in] struct AllocInfo info, [out] NativeBuffer handle) | 内存申请接口。 |
| [ReAllocMem](#reallocmem) ([in] struct AllocInfo info, [in] NativeBuffer inHandle, [out] NativeBuffer outHandle) | 二次申请内存接口。 |
| [IsSupportAllocPassthrough](#issupportallocpassthrough) ([in] struct AllocInfo info) | 直通模式调用判断接口。 |

## 成员函数说明

### AllocMem()

```idl
IMapper::AllocMem([in] struct AllocInfo info, [out] NativeBuffer handle)
```

**描述**

内存申请接口。

**起始版本：**  6.0

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| info | 内存申请规格相关信息。 |
| handle | 返回的内存。 |

**返回：**

返回0，表示执行成功。

返回其他值表示执行失败，具体错误码查看[DispErrCode](_display_v10.md#disperrcode)。

### IsSupportAllocPassthrough()

```idl
IMapper::IsSupportAllocPassthrough([in] struct AllocInfo info)
```

**描述**

直通模式调用判断接口。

**起始版本：**  6.0

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| info | 内存申请规格相关信息。 |

**返回：**

返回0，表示执行成功。

返回其他值表示执行失败，具体错误码查看[DispErrCode](_display_v10.md#disperrcode)。

### ReAllocMem()

```idl
IMapper::ReAllocMem([in] struct AllocInfo info, [in] NativeBuffer inHandle, [out] NativeBuffer outHandle)
```

**描述**

二次申请内存接口。

**起始版本：**  6.0

**参数:**

| 名称 | 描述 |
| -------- | -------- |
| info | 二次内存申请规格相关信息。 |
| inHandle | 首次申请的内存大小。 |
| outHandle | 二次申请内存大小。 |

**返回：**

返回0，表示执行成功。

返回其他值表示执行失败，具体错误码查看[DispErrCode](_display_v10.md#disperrcode)。
