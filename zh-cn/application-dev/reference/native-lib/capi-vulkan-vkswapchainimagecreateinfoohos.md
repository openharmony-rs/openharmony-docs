# VkSwapchainImageCreateInfoOHOS

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphic-->
<!--Owner: @andrew1993-->
<!--Designer: @ext4FAT1-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->

```c
typedef struct VkSwapchainImageCreateInfoOHOS {...} VkSwapchainImageCreateInfoOHOS
```

## 概述

包含创建Image时必要的参数。

**起始版本：** 10

**相关模块：** [Vulkan](capi-vulkan.md)

**所在头文件：** [vulkan_ohos.h](capi-vulkan-ohos-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| VkStructureType sType | 结构体类型。 |
| const void*                       pNext | 下一级结构体指针，pNext为空或者下一级结构体指针。 |
| VkSwapchainImageUsageFlagsOHOS usage | 交换链图像的使用标志。 |