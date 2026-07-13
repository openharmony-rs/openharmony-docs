# ArkUI_ContextCallback

```c
typedef struct ArkUI_ContextCallback {...} ArkUI_ContextCallback
```

## 概述

Defines the event callback type.

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_type.h](capi-native-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| void* userData | Custom type, data of a user-defined type that is passed as a parameter during callbacks. |


### 成员函数

| 名称 | 描述 |
| -- | -- |
| [void (\*callback)(void* userData)](#callback) | Event callback. |

## 成员函数说明

### callback()

```c
void (*callback)(void* userData)
```

**描述**

Event callback.


