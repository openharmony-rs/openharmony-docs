# JSVM_PropertyDescriptor

```c
typedef struct JSVM_PropertyDescriptor {...} JSVM_PropertyDescriptor
```

## 概述

属性描述符。

<!--Device-typedef struct JSVM_PropertyDescriptor {...} JSVM_PropertyDescriptor--><!--Device-typedef struct JSVM_PropertyDescriptor {...} JSVM_PropertyDescriptor-End-->

**系统能力：** SystemCapability.ArkCompiler.JSVM

**起始版本：** 11

**相关模块：** [JSVM](capi-arkts-jsvm.md)

**所在头文件：** [jsvm_types.h](capi-jsvm-types-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| const char* utf8name | 描述属性键值的可选字符串，UTF8编码。 必须为属性提供utf8name或name之一。<br><!--Device-const char* utf8name--><!--Device-const char* utf8name-End--> |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) name | 可选的JSVM_Value，指向用作属性键的JavaScript字符串或符号。 必须为属性提供utf8name或name之一。<br><!--Device-JSVM_Value name--><!--Device-JSVM_Value name-End--> |
| JSVM_Callback method | 设置此项使属性描述符对象的value属性成为method表示的JavaScript函数。<br><!--Device-JSVM_Callback method--><!--Device-JSVM_Callback method-End--> |
| JSVM_Callback getter | 执行对属性的获取访问时调用的函数。<br><!--Device-JSVM_Callback getter--><!--Device-JSVM_Callback getter-End--> |
| JSVM_Callback setter | 执行属性的设置访问时调用的函数。<br><!--Device-JSVM_Callback setter--><!--Device-JSVM_Callback setter-End--> |
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | 如果属性是数据属性，则通过属性的get访问检索到的值。<br><!--Device-JSVM_Value value--><!--Device-JSVM_Value value-End--> |
| [JSVM_PropertyAttributes](capi-jsvm-types-h.md#jsvm_propertyattributes) attributes | 与特定属性关联的属性。<br><!--Device-JSVM_PropertyAttributes attributes--><!--Device-JSVM_PropertyAttributes attributes-End--> |


