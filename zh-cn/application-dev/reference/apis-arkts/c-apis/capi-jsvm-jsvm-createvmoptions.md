# JSVM_CreateVMOptions

```c
typedef struct JSVM_CreateVMOptions {...} JSVM_CreateVMOptions
```

## 概述

创建JavaScript虚拟机的选项。

<!--Device-typedef struct JSVM_CreateVMOptions {...} JSVM_CreateVMOptions--><!--Device-typedef struct JSVM_CreateVMOptions {...} JSVM_CreateVMOptions-End-->

**系统能力：** SystemCapability.ArkCompiler.JSVM

**起始版本：** 11

**相关模块：** [JSVM](capi-arkts-jsvm.md)

**所在头文件：** [jsvm_types.h](capi-jsvm-types-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| size_t maxOldGenerationSize | 老年代内存大小上限。<br><!--Device-size_t maxOldGenerationSize--><!--Device-size_t maxOldGenerationSize-End--> |
| size_t maxYoungGenerationSize | 年轻代内存大小上限。<br><!--Device-size_t maxYoungGenerationSize--><!--Device-size_t maxYoungGenerationSize-End--> |
| size_t initialOldGenerationSize | 老年代内存大小初始值。<br><!--Device-size_t initialOldGenerationSize--><!--Device-size_t initialOldGenerationSize-End--> |
| size_t initialYoungGenerationSize | 年轻代内存大小初始值。<br><!--Device-size_t initialYoungGenerationSize--><!--Device-size_t initialYoungGenerationSize-End--> |
| const char* snapshotBlobData | 启动快照数据。<br><!--Device-const char* snapshotBlobData--><!--Device-const char* snapshotBlobData-End--> |
| size_t snapshotBlobSize | 启动快照数据的大小。<br><!--Device-size_t snapshotBlobSize--><!--Device-size_t snapshotBlobSize-End--> |
| bool isForSnapshotting | 虚拟机是否用于创建快照，为true，则虚拟机用于创建快照，为false，则虚拟机不用于创建快照。<br><!--Device-bool isForSnapshotting--><!--Device-bool isForSnapshotting-End--> |


