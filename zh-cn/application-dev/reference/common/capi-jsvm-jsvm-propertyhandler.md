# JSVM_PropertyHandler
<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->

```c
typedef struct {...} JSVM_PropertyHandler
```

## 概述

包含将class作为函数进行调用时所触发的回调函数的函数指针，以及访问实例对象属性时触发的回调函数的函数指针集。

**使用场景：** 用于拦截和自定义对象的函数调用行为，用于实现属性访问的自定义逻辑。

**功能特点：** 支持在实例对象作为函数调用时触发自定义回调，支持在访问实例对象属性时触发相应的回调函数。

**能解决的问题：** 实现对象的代理模式，自定义函数调用行为。提供属性访问的拦截机制，增强代码的灵活性和可扩展性。

**系统能力：** SystemCapability.ArkCompiler.JSVM

**起始版本：** 18

**支持设备类型：** Phone | PC/2in1 | Tablet | Wearable。具体支持情况可通过对应的API接口进行判断。

**相关模块：** [JSVM](capi-jsvm.md)

**所在头文件：** [jsvm_types.h](capi-jsvm-types-h.md)

## 汇总

### 成员变量

| 名称                                                                                                  | 描述 |
|-----------------------------------------------------------------------------------------------------| -- |
| [JSVM_PropertyHandlerCfg](capi-jsvm-jsvm-propertyhandlerconfigurationstruct8h.md) propertyHandlerCfg | 访问实例对象属性触发相应的回调函数。 |
| [JSVM_Callback](capi-jsvm-jsvm-callbackstruct8h.md) callAsFunctionCallback                                                            | 实例对象作为函数调用将触发此回调。 |


