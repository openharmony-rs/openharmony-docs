# RawFileDescriptor

## 概述

提供rawfile文件描述符信息。RawFileDescriptor是[OH_ResourceManager_GetRawFileDescriptor](capi-raw-file-h.md#oh_resourcemanager_getrawfiledescriptor)的输出参数,涵盖了rawfile文件的文件描述符以及在HAP包中的起始位置和长度。

**起始版本：** 8

**相关模块：** [rawfile](capi-rawfile.md)

**所在头文件：** [raw_file.h](capi-raw-file-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| int fd | rawfile文件描述符，单位为int。 |
| long start | rawfile在HAP包中的起始位置，单位为long。 |
| long length | rawfile在HAP包中的长度，单位为long。 |


