# boardinfo.h
<!--Kit: Basic Services Kit-->
<!--Subsystem: Startup-->
<!--Owner: @chenjinxiang3-->
<!--Designer: @chenjinxiang3-->
<!--Tester: @liuhaonan2-->
<!--Adviser: @fang-jinxu-->

## 概述

声明用于查询硬件设备信息的API。

**引用文件：** <boardinfo.h>

**库：** libboardinfo.so

**系统能力：** SystemCapability.Startup.BoardInfo

**起始版本：** 26.1.0

**相关模块：** [BoardInfo](capi-boardinfo.md)

## 汇总

### 函数

| 名称 | 描述 |
| -- | -- |
| [const char *OH_BoardInfo_GetCpuId(void)](#oh_boardinfo_getcpuid) | 获取设备CPUID。 |
| [int32_t OH_BoardInfo_GetBoardSn(char *boardSn)](#oh_boardinfo_getboardsn) | 获取设备Sn.value len为16。参数缓冲区容量不能低于17字节(包含结束符)。 |

## 函数说明

### OH_BoardInfo_GetCpuId()

```c
const char *OH_BoardInfo_GetCpuId(void)
```

**描述**

获取设备CPUID。

**起始版本：** 26.1.0

**返回：**

| 类型 | 说明 |
| -- | -- |
| const char* | 返回设备CPUID。字符串类型。 |

### OH_BoardInfo_GetBoardSn()

```c
int32_t OH_BoardInfo_GetBoardSn(char *boardSn)
```

**描述**

获取设备Sn.value len为16。参数缓冲区容量不能低于17字节(包含结束符)。

**需要权限：** ohos.permission.ACCESS_BOARD_INFO

**参数：**

| 参数名 | 说明 |
| --  | -- |
| char* boardSn | 单板序列号。缓冲区容量不能低于17字节(包含结束符)。 |

**起始版本：** 26.1.0

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | <ul><li>如果操作成功，则返回0。</li><li>201如果调用者没有ohos.permission.ACCESS_BOARD_INFO。</li><li>401如果调用者传入的入参为空或非法。</li></ul> |
