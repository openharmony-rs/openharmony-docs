# native_fence.h
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @Felix-fangyang-->
<!--Designer: @conan13234-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
## 概述

定义获取和使用NativeFence的相关函数。NativeFence用于图形系统中的同步控制，支持检查fence有效性、阻塞等待fence信号、关闭fence等操作，适用于多线程或多进程间需要同步图形资源访问的场景。

**引用文件：** <native_fence/native_fence.h>

**库：** libnative_fence.so

**起始版本：** 20

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeWindow

**相关模块：** [NativeFence](capi-nativefence.md)

## 汇总

### 函数

| 名称                                                         | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [bool OH_NativeFence_IsValid(int fenceFd)](#oh_nativefence_isvalid) | 检查fenceFd是否有效。                                        |
| [bool OH_NativeFence_Wait(int fenceFd, uint32_t timeout)](#oh_nativefence_wait) | 阻塞传入的fenceFd。最大阻塞时间由超时参数决定。传入的fenceFd需要用户自己关闭。 |
| [bool OH_NativeFence_WaitForever(int fenceFd)](#oh_nativefence_waitforever) | 永久阻塞传入的fenceFd。传入的fenceFd需要用户自己关闭。       |
| [void OH_NativeFence_Close(int fenceFd)](#oh_nativefence_close) | 关闭fenceFd。                                                |

## 函数说明

### OH_NativeFence_IsValid()

```c
bool OH_NativeFence_IsValid(int fenceFd)
```

**描述**

检查fenceFd是否有效。

**起始版本：** 20


**参数：**

| 参数项      | 描述                               |
| ----------- | ---------------------------------- |
| int fenceFd | 表示一个文件描述符，用于定时同步。 |

**返回：**

| 类型 | 说明                                                     |
| ---- | -------------------------------------------------------- |
| bool | 返回true表示fenceFd有效，返回false表示该值是一个负整数。 |

### OH_NativeFence_Wait()

```c
bool OH_NativeFence_Wait(int fenceFd, uint32_t timeout)
```

**描述**

阻塞传入的fenceFd。最大阻塞时间由超时参数决定。传入的fenceFd需要用户自己关闭。


**起始版本：** 20


**参数：**

| 参数项           | 描述                                                         |
| ---------------- | ------------------------------------------------------------ |
| int fenceFd      | 表示一个文件描述符，用于定时同步。                           |
| uint32_t timeout | 表示等待时间。大于0的值表示具体等待时长（适用于需要限制等待时间的场景，推荐根据实际业务需求设置合理超时值）；0表示接口立即返回（适用于仅检查fenceFd状态而不阻塞的场景）；如需永久等待，请使用[OH_NativeFence_WaitForever](#oh_nativefence_waitforever)接口。 |

**返回：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| bool | 返回true表示对应的fenceFd有信号触发；<br>在以下情况会返回false：<br>1.传入的fenceFd为负整数。<br>2.在指定的超时时间内无信号触发。<br>3.调用底层poll接口失败。<br>4.超时时间设置为0。<br>5.接口中复制文件描述符执行失败。 |

### OH_NativeFence_WaitForever()

```c
bool OH_NativeFence_WaitForever(int fenceFd)
```

**描述**

永久阻塞传入的fenceFd。传入的fenceFd需要用户自己关闭。

**起始版本：** 20


**参数：**

| 参数项      | 描述                               |
| ----------- | ---------------------------------- |
| int fenceFd | 表示一个文件描述符，用于定时同步。 |

**返回：**

| 类型 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| bool | 返回true表示对应的fenceFd有信号触发；<br>在以下情况会返回false：<br>1.传入的fenceFd为负整数。<br>2.在指定的超时时间内无信号触发，永久等待。<br>3.接口中复制文件描述符执行失败。 |

### OH_NativeFence_Close()

```c
void OH_NativeFence_Close(int fenceFd)
```

**描述**

关闭fenceFd。

**起始版本：** 20


**参数：**

| 参数项      | 描述                                                   |
| ----------- | ------------------------------------------------------ |
| int fenceFd | 表示一个文件描述符，用于定时同步。该值是一个非负整数。 |

