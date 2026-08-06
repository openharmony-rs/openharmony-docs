# ArkUI_ContextCallback

```c
typedef struct ArkUI_ContextCallback {...} ArkUI_ContextCallback
```

## 概述

事件回调类型，用于定义回调函数及其用户自定义数据。使用该类型的接口触发回调时，会调用callback，并将userData作为参数传入。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [common_type.h](capi-common-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| void* userData |  |


### 成员函数

| 名称 | 描述 |
| -- | -- |
| [void (\*callback)(void* userData)](#callback) |  |

## 成员函数说明

### callback()

```c
void (*callback)(void* userData)
```

**描述**


