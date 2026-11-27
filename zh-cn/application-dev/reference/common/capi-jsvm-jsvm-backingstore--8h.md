# JSVM_BackingStore__*
<!--Kit: ArkTS-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @k1ngqaquuu-->

```c
typedef struct JSVM_BackingStore__* JSVM_BackingStore
```

## 概述

表示一个与虚拟机无关的共享内存（BackingStore）句柄。句柄持有对SharedArrayBuffer底层内存的一个独立引用，在源SharedArrayBuffer对象或源虚拟机销毁后依然有效，可以在同一进程内的其他JSVM虚拟机中重建SharedArrayBuffer。通过[OH_JSVM_GetSharedArrayBufferBackingStore](capi-jsvm-h.md#oh_jsvm_getsharedarraybufferbackingstore)或[OH_JSVM_RetainBackingStore](capi-jsvm-h.md#oh_jsvm_retainbackingstore)获取的每个句柄，都必须调用[OH_JSVM_ReleaseBackingStore](capi-jsvm-h.md#oh_jsvm_releasebackingstore)释放一次。

**系统能力：** SystemCapability.ArkCompiler.JSVM

**起始版本：** 26.1.0

**相关模块：** [JSVM](capi-jsvm.md)

**所在头文件：** [jsvm_types.h](capi-jsvm-types-h.md)
