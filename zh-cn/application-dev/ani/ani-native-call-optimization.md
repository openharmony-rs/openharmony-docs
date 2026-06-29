# Native调用性能优化注解
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @wanzixuan330-->
<!--Designer: @LeechyLiang; @zengmanyi; @jcj525-->
<!--Tester: @wuhan544-->
<!--Adviser: @fang-jinxu-->

## Native调用模式

ArkTS-Sta支持以下native调用模式：
- 默认模式（无注解）：完整的托管-本地边界处理，包括协程状态切换，以便正确管理GC Root和异常。
- 添加`@ani.unsafe.Quick`注解：不切换到native状态，节省UpdateStates状态切换的耗时，线程保持RUNNABLE状态，阻塞GC。

## `@ani.unsafe.Quick`注解

开发者只需在ets侧被标记为native的方法上添加`@ani.unsafe.Quick`注解即可，其他方法绑定、C++侧方法实现等操作与常规的native方法调用一致。

**`@ani.unsafe.Quick`示例代码：**
```ts
// ets侧 native方法添加@ani.unsafe.Quick注解
class Test {
    @ani.unsafe.Quick
    native ProcBoolArray(a: FixedArray<boolean>, length: int): void;
}
```

```cpp
// C++侧 方法实现
static void ProcBoolArray(ani_env *env, [[maybe_unused]] ani_object object, ani_fixedarray_boolean arr, ani_int length)
{
    ani_size size = length;
    std::vector<ani_boolean> nativeBuffer(size);
    env->FixedArray_GetRegion_Boolean(arr, 0, size, nativeBuffer.data());
    ani_boolean value0;
    for (ani_size i = 0; i < size ; i++) {
        value0 = nativeBuffer[i];
    }
}
```

### 使用场景

添加`@ani.unsafe.Quick`注解会阻塞GC，所以只适用于**逻辑短、快、可控**的接口场景。

**注解不能使用的场景：**

一个native接口运行时间很长或者涉及读文件、联网相关的操作，不可以使用此注解。

