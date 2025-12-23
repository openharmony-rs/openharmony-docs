# VkExternalFormatOHOS

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphic-->
<!--Owner: @andrew1993-->
<!--Designer: @ext4FAT1-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->

```c
typedef struct VkExternalFormatOHOS {...} VkExternalFormatOHOS
```

## 概述

表示外部定义的格式标识符。

**起始版本：** 10

**相关模块：** [Vulkan](capi-vulkan.md)

**所在头文件：** [vulkan_ohos.h](capi-vulkan-ohos-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| VkStructureType sType | 结构体类型，值必须为VK_STRUCTURE_TYPE_EXTERNAL_FORMAT_OHOS。 |
| void* pNext | pNext为空或者下一级结构体指针。 |
| uint64_t externalFormat | 外部定义的格式标识符。 |


