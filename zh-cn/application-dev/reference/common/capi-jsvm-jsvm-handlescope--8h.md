# JSVM_HandleScope__*
<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->

```c
typedef struct JSVM_HandleScope__* JSVM_HandleScope
```

## 概述

表示JavaScript值的作用域，用于控制和修改在特定范围内创建的对象的生命周期。通常，JSVM-API值是在JSVM_HandleScope的上下文中创建的。当从JavaScript调用native方法时，将存在默认JSVM_HandleScope。如果用户没有显式创建新的JSVM_HandleScope，将在默认JSVM_HandleScope中创建JSVM-API值。对于native方法执行之外的任何代码调用（例如，在libuv回调调用期间），模块需要在调用任何可能导致创建JavaScript值的函数之前创建一个作用域。JSVM_HandleScope是使用OH_JSVM_OpenHandleScope创建的，并使用OH_JSVM_CloseHandleScope销毁的。关闭作用域代表向GC指示在JSVM_HandleScope作用域的生命周期内创建的所有JSVM_Value将不再从当前堆的栈帧中引用。

**配对调用：** 必须成对调用OH_JSVM_OpenHandleScope()和OH_JSVM_CloseHandleScope()，每次调用OH_JSVM_OpenHandleScope()后，必须在使用完毕后调用OH_JSVM_CloseHandleScope()释放资源。

**违反后果：** 如果忘记调用OH_JSVM_CloseHandleScope()，会导致内存泄漏和资源无法释放。

**使用场景：** 在Native方法中创建JSVM-API值，在libuv回调等非native方法执行期间调用可能创建JavaScript值的函数，需要精确控制JavaScript对象生命周期。

**收益：** 避免内存泄漏：通过作用域管理对象生命周期，防止不必要的内存占用。提高GC效率：明确指示GC哪些对象可被回收，减少垃圾回收开销。

**系统能力：** SystemCapability.ArkCompiler.JSVM

**起始版本：** 11

**支持设备类型：** Phone | PC/2in1 | Tablet | Wearable。具体支持情况可通过对应的API接口进行判断。

**相关模块：** [JSVM](capi-jsvm.md)

**所在头文件：** [jsvm_types.h](capi-jsvm-types-h.md)

