# JSVM_VMInfo

```c
typedef struct JSVM_VMInfo {...} JSVM_VMInfo
```

## 概述

JavaScript虚拟机信息。

<!--Device-typedef struct JSVM_VMInfo {...} JSVM_VMInfo--><!--Device-typedef struct JSVM_VMInfo {...} JSVM_VMInfo-End-->

**系统能力：** SystemCapability.ArkCompiler.JSVM

**起始版本：** 11

**相关模块：** [JSVM](capi-arkts-jsvm.md)

**所在头文件：** [jsvm_types.h](capi-jsvm-types-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t apiVersion | 此虚拟机支持的最高API版本。<br><!--Device-uint32_t apiVersion--><!--Device-uint32_t apiVersion-End--> |
| const char* engine | 实现虚拟机的引擎名称。<br><!--Device-const char* engine--><!--Device-const char* engine-End--> |
| const char* version | 虚拟机的版本。<br><!--Device-const char* version--><!--Device-const char* version-End--> |
| uint32_t cachedDataVersionTag | 缓存数据版本标签。<br><!--Device-uint32_t cachedDataVersionTag--><!--Device-uint32_t cachedDataVersionTag-End--> |


