# syscap_ndk.h

## 概述

Declares APIs for acquiring the set of system capabilities .

**库：** NA

**系统能力：** SystemCapability.Startup.SystemInfo

**起始版本：** 10

**相关模块：** [SyscapNdk](capi-syscapndk.md)

## 汇总

### 函数

| 名称 | 描述 |
| -- | -- |
| [bool canIUse(const char *cap)](#caniuse) | 查询单个系统能力是否被支持的API。 |

## 函数说明

### canIUse()

```c
bool canIUse(const char *cap)
```

**描述**

查询单个系统能力是否被支持的API。

**起始版本：** 8

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char *cap | SystemCapability whether supported |

**返回：**

| 类型 | 说明 |
| -- | -- |
| bool | 查询指定的系统能力是否被支持。<br>     <br>系统能力（SystemCapability，简称SysCap），指操作系统中每一个相对独立的特性。不同的设备对应不同的系统能力集，每个系统能力对应一个或多个API。开发者可根据系统能力来判断是否可以使用某接口。 |


